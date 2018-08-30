## Background Processing: an Unexpected Journey

There will be dragons

* Session: https://360idev.com/sessions/background-processing-what-a-long-strange-trip/

* Slides: https://docs.google.com/presentation/d/1nY046Hv-ke9nHVtGn2-GcBa-oFJzgXcCRCHU_YFihM0/edit

#### Synopsis
Before you decide to add background processing to your app, come learn about our long, strange, but successful trip of getting background processing fully baked into our iOS app. We used background processing to pre-fetch data and fire notifications, but after a quick initial implementation, we discovered all kinds of gotchas that gave our developers’ and QA team’s hair a touch of grey. We’ll also share lessons learned comparing our iOS app to our Android app notification tap-through rates and behavior changes after we launched our background processing functionality.

### Author

**Karl Becker**

[@karlbecker_com](@karlbecker_com)

* CTO of ThirdIron (thirdiron.com)

* Product is BrowZine (browzine.com)

Used by academics, hospitals, and others who use private journals / libraries.  Kind of like an RSS feed for relevant journals.

Join Mastodon: mastodon.social/invite/rzqpmUkh

### Primary goal

Notifications of new and unread articles.  

Protected by dragons.

#### Why Push Notifications

iOS team had more capacity than back-end team and initial dev seemed quick.

Secondary goal: less loading screens

#### Initial implementation

Very quick initial implementation.  But didn't ship for months.  Why?

Time to test was 5x typical feature.

### Testing

**Why did it take so long?**

App specific stuff was meant to be slow and long-lived.  Academic journals take time.  It's not like Twitter with lots of events happening at all times.  Sometimes journals take weeks or months.  And devices can sit for weeks without being opened.  That takes a lot of real-world time to validate.

#### iOS & Android UX differences

Cross-platform apps need to consider implementation differences and expectations.

Dragons:
* Apple made major changes in iOS 12
* iOS 9.  Advice; avoid iOS 9 background fetch.  It's terrible.
* No guarantee that the system will give your app any time to perform background fetches

### What to do

* Be memory thrifty.  Smallest footprint you can.
* Reduce network calls by storing data on disk or keychain

If using background fetch API, be accurate and quick

* Call the completion handler in a timely manner.  If it takes too long, apple with throttle you.

* Avoid view logic!

* Use BackgroundTask

Eskimo (apple developer forum user) has a good post about the eccentricities of BackgroundTask

Note that background fetch may start when app in foreground, so check application.applicationState explicitly if you don't want fg processing.

Background processing might be interrupted by an app launch.  Don't let that happen.

* Beware Force Close

* Beware XCode Run

Don't run the app from XCode.  Tap the icon in your device instead.

* Beware airplane mode and wifi only

Background processes will not run!  (...in their experience)

### General erraticness

Not fun for QA.  

OS decides when to do things.  "The algorithm it uses is complex"

XCode Simulate Background Fetch will check if the code itself works.  To see if it works in practice, you'll just have to wait.

### File access

Files may not be available during bg processing

* Including NSUserDefaults

* NSUserDefaults may even look empty

If app is launched in the background then goes to the foreground, NSUserDefaults is empty!

They tried NSUserDefaults.resetStandardUserDefaults and .standard.synchronize() and still have problems.

### Gold

Notifications did increase usage!  Users open the app 20% more often.

Android notifications get 3x as many taps.
