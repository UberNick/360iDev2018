## Background Processing: an Unexpected Journey

There will be dragons

* Session: https://360idev.com/sessions/background-processing-what-a-long-strange-trip/

### Author

Karl Becker CTO of ThirdIron
Product is BrowZine

Used by academics, hospitals, and others who use private journals / libraries.  Kind of like an RSS feed for relevant journals.

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
