# How I Learned to Stop Worrying and Love Voiceover
#### Speaker: [Rachel Hyman](https://360idev.com/speakers/rachel-hyman/)
* The goal is to make your app usable by everyone.
* Apple's Voiceover accessibility feature is basically a screen reader.

#### UIAccessibilityProtocol
Items in your app are made visible to the accessibility tools via by implementing the UIAccessibility protocol.

#### Tips
Xcode has an accessibility inspector tool. This tool runs an audit of your app and raises potential issues and warnings.
You can use this tool, but often the best way to spot issues is by simply using your app with the accessibility tools enabled.

Keep in mind flow and discoverability when thinking about accessibility.

#### Dynamic Type
Size fonts more by categories rather than specific point sizes. By doing this, if users increase or decrease font size the information hierarchy of your app is maintained.

Enable the "Dynamic Type Automatically Adjusts Font" checkbox in IB to allow labels to adjust dynamically.