## Customizing Your Notification for iOS 12

* Session: https://360idev.com/sessions/customizing-your-notifications-for-ios-12/

* Demo: https://github.com/kmt901/Notifications-iOS12

### Author

**Kaya Thomas**

@kthomas91

kayathomas.info

Works at Slack focusing on messenging and accessibility.  Also worked at Apple in acccessibility.

### Agenda

Overview, Demo, Authorization Options, Grouped Ntoifications, Dynamic Catagory

### Remote Push Notification

Two kinds of notifications.  Remote push and local push.

To send remote notifications, you need a push note certificate and a device token.  So for ease of this talk, we'll use local notifications and send them directly from the apps.

### Local Notifications

Create & scheudle notifications directly from the app.

To get the calendar to notify:
`dateComponents = DateComponents() //...`
`let trigger = UICalendarNotificationTrigger(dataMatching: )`
`let request = UNNotificationRequest(...)`

### Notification Service Extension

Separate target where you can modify data from incoming notification before it reaches device.  

Example:

* Decrypt data before hitting apps

You can use an app extension that manages a VC to customize the look and content of the notifications.  Don't have to go into the app.

### Demo

Simply app to send a notification.

Content extension to show it.

### What's New in iOS 12?

* Authorization options

Ability for users to manage notification settings directly from the notifications too.

Including "deliver quietly" options where it'll just show up in the notification center.

You can do that with Provisional Authorization

#### Provisional Authorization

Provisional Authorization allows you to send notifications without first asking for permission.  But they show up quietly.

How to?

`UNUserNotificationCenter.current().requestAuthorizations(options: [...provisional: true])`

### App Notification Settings

Users can also turn it off from the notification.  Also a deep link to the notification settings within the app itself.

### Grouped Notifications

Grouping can be determined by the dev, or set by the user (to app only.)

So even if as a dev you customize it, users can override.

#### Thread Identifier

Thread Identifier is a string payload.  That's where you set grouped settings.

And Set a **Group Notification Summary** like "3 more episodes available"

Notification Categories are a template

### Summary

Start by setting provisional notifications, so you don't have to initially ask user.

Set a deep link to your notification settings.

Know that custom settings can be override.

Set up action callbacks for user.
