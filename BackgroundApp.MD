## The complicated Life of a Backgrounded iOS App

* Session: https://360idev.com/sessions/the-complicated-life-of-a-backgrounded-ios-app/

### Author

**Agnes Vasarhelyi**

### Purpose

Goal is to show what caused the most headaches in the weeks it took to figure out what's happening in the background, and save us from those.

### App States

Not running -> Forground(Inactive <- -> Active) -> Background(Inactive)

"Backgroud apps that consume large amounts of memory are terminated before those with small memory footprints" -Apple

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

#### Silent push

Silent push notifications with content-available flag set

***Surprises***:
* User can switch it off with Settings / Background Refresh.
* Rate limited by APNS (no more that 2/3 per hour)
* Doesn't work when app terminated

"The system tracks the elapsed time"

"Apps...(using a lot of memory)... may not always be woken up" for notifications to come.

### Authentication

Cert pinning caused some issues.  ATS requirement is that only system-trusted CA-signed-certs.  Rolling certs means public key is static, along with backup keys (to avoid risk of downtime).

### Resume rate limiter

* Delay that doubles with each resume
* It resets to 0 when user returns to app
* Applies to whole app not one download

Note that each custom authentication challenge will mean a doubled delay.
