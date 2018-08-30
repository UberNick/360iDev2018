# Firing on all cylinders: A breakdown of Firebase on iOS
Niamh Power - [@niamh__power](https://twitter.com/niamh__power)

### What on earth is Firebase?
* Started as a database solution.
* Now a suite of backend tools (database, analytics, etc) for app development

##### Example App: Lunch Train
* Based on the Slack bot for coordinating where groups are going for lunch

### Step 1: Authentication
* Provides easy integration with most auth services (google, facebook etc)
* Anonymous login
    * Allows an anonymous "profile" of sorts, which will be integrated into a created user once that user creates an authenticated account

### Step 2: Data Management
* Firebase Cloud Firestore
    * Data, documents, and collections
        * Collections contain documents, documents contain data
    * More scalable than realtime database
* Writing data
    * Create structs that match your backend "documents"
    * Extend your structs to `DocumentSerializable`
        * ?? Does this conform to `Codable` ??
* Offline support
    * Cloud Firestore automatically handles loss of connection + state + resolving state
* Security Rules
    * ?? Written client-side or on the backend ??

### Step 3: Notifications
* Firebase Cloud Messaging
    * Notifications Console interface on backend dashboard
    * Firebase has built-in A/B testing, which will allow you to find the correct kind of notifications for your app
* Cloud Functions
    * Code that can be triggered and run on the backend (kind of like Lambdas)
