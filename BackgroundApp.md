## The complicated Life of a Backgrounded iOS App

* Session: https://360idev.com/sessions/the-complicated-life-of-a-backgrounded-ios-app/

### Author

**Agnes Vasarhelyi**

### Purpose

Goal is to show what caused the most headaches in the weeks it took to figure out what's happening in the background, and save us from those.

### App States

Not running -> Foreground(Inactive <- -> Active) -> Background(Inactive)

"Background apps that consume large amounts of memory are terminated before those with small memory footprints" -Apple

Only pointed out in high-level documentation.  As developers, our apps are pretty limited in what control we have.

### URLSessionAPI
We'll have to move away from completion-handler based calls

And move on toward delegate-based calls

The reason is that iOS runs them in a separate process

Surprises:
* Storing session IDs
* Storing completion handlers (in case app gets killed)
* Tasks are not failing! (very surprised)

"For time-**insensitive** tasks, enable the isDiscretionary property"

The OS can wait for things like better bandwidth or battery charge before proceeding.  Maybe 12 hours later.  That can be annoying because we don't have more control over background features than this.

If your app requests data (file download for example) your app could be suspended while waiting. If this happens, the system can launch your app again in the background to hand off the data.

### Silent Push

Silent push is when your app receives a notification in the background, the system resumes your app, and does some work in the background.

Major takeaway is due to it's occasionally unreliable nature, don't build critical functionality on silent push.

Silent push notifications with content-available flag set

***Surprises***:
* User can switch it off with Settings / Background Refresh.
* Rate limited by APNS (no more that 2/3 per hour)
* Doesn't work when app terminated

"The system tracks the elapsed time"

"Apps...(using a lot of memory)... may not always be woken up" for notifications to come.

### Authentication

Cert pinning caused some issues. ATS requirement is that only system-trusted CA-signed-certs. Rolling certs means public key is static, along with backup keys (to avoid risk of downtime).

It's recommended to implement a custom authentication scheme, where you ask for an app token in the foreground session.

### Resume Rate Limiter

* Delay that doubles with each resume
* It resets to 0 when user returns to app
* Applies to whole app not one download

Note that each custom authentication challenge will mean a doubled delay.

You can make it happy by batching the transfers and using an auth model that doesn't require additional resumes.

### Testing

Testing is difficult.

***Surprises***
* Free pass for XCode builds (resume rate limiter delays and isDiscretionary flags are disabled for these test builds).
* APNS device token only valid in specific environments.
* Call registerForRemoteNotifications App Delegate method on every launch.

**Console.app**

* Look at nsurlsessiond logs for networking.
* Look at dasd logs for scheduling.
* Search for your bundle ID to filter results.
* Then put the pieces together...

### Tips

* Only use it for time insensitive work
* Design networking layer in a way to please the RRL (including auth)
* Master using Console.app
