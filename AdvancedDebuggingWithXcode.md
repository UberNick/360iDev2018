# Advanced Debugging With Xcode - Extending LLDB

[Aijaz Ansari](https://360idev.com/speakers/aijaz-ansari/) - Mobile Application team lead at Gogo Business Aviation

### Breakpoint Actions
Using breakpoint actions you can inject code using the `expr` LLDB command.
1. Add breakpoint
2. Edit breakpoint > add debugger action > debugger command
3. Add expression: `expr self.myLabel.text = "foo"`
4. Check checkbox to auto-continue if you don't want the debugger to pause.

_Note to self_: Look into `type summary add`... command in LLDB. This changes how LLDB reports info. It can be used to make it much more useful.

### `.lldbinit`
In your home directory you can create an `.lldbinit` config file to inject stuff when LLDB starts up. (For example, the `type summary add`... command.)

### Scripting LLDB
LLDB is scriptable with Python.

Using debugger actions tied to breakpoints, you can invoke Python scripts to give custom behaviors to LLDB and do stuff like custom formatting for printing out values of specific types, etc.
For example, if you have a complex Swift object, you can use this to create a nice, easily readable print-out value.

_Note to self_: Check out the JSON parsing tool `jq`. It's a powerful command line tool to grep and filter through JSON files.

### Resources
Presenter's repo of Python scripts and `.lldbinit` can be found at: https://github.com/aijaz/lldbPythonScripts

Lots of good WWDC talks on LLDB and debugging with Xcode as well:
* WWDC 2018: [Advanced Debugging with Xcode and LLDB](https://developer.apple.com/videos/play/wwdc2018/412/)
* WWDC 2017: [Debugging with Xcode 9](https://developer.apple.com/videos/play/wwdc2017/404/)


#### Helpful Command
From the command line, open an `.xcodeproj` or `.xcworkspace` file in the current directory:
```
$ xed .
```
