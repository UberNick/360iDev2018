## State of Swift Internals: Swift 4 & 5

* Session: https://360idev.com/sessions/state-of-swift-internals-swift-4-5/

* Code: https://github.com/sptramer/360idev-2018-swift

* Summary:

Hey, what’s going on with the Swift compiler these days? How does it work with other libraries on my system? Does it follow the System V calling conventions yet? What about sneaky tricks to get data I normally can’t into Objective-C? What’s this ‘lifetimes’ thing people talk about sometimes? Is ABI stability a thing yet, and why should I care?

In this update of the 360iDev 2014 and 2016 talks on Swift interoperability, you’ll learn a lot about how the Swift compiler works, how it can link to libraries from another language, and even how well it works on non-Apple platforms right now (and what you can do to make it better.)

### Author

**Stephen Tramer**

### Purpose

~On the Swift Compiler~

Steve Reads Source and Docs (~so you don't have to~ so you can too)

Roadmap: Why? Compilation stages. ABI stability (data layouts, calling, library guarantees, swift 5), FFI

### Why should we care?

Apple claims Swift is a "systems programming language" which is not true.  It's an application programming language.  So let's look at the difference.

Demystifying compilers.  Sounds super complicated and esoteric, but really it's just a program that takes input and gives output.  Open swift compiler like Golang and C++.

Swift breaks a lot of API rules.  Doesn't happen elsewhere.  Why and what they mean is important.

### Compiler Pipeline

* Swift -> Swift Intermediate Languge (SIL)

SIL is somewhere between swift and assumbly.

* SIL -> LLVM IR (LLVM Intermediate Representation, aka bitcode)

* LLVM IR -> ASM

Swift -> SIL comes you can see with:

`swiftc -emit-silgen`

`swiftc -emit-sil`

### ABI Stability

That ensures that two pieces of software, built with different versions of the compiler, at different times, can still link together.  This will allow us to ship a binary framework.

Good for future-proofing and longevity.  If you're working in iOS15 and need to compile for iOS13, you can use the same app as long as you don't call anything that's been introduced as a new method.

### Data Layouts

Swift 4.2 has locked data layouts.  Only 6-8 months work to complete ABI stability.

Only thing that isn't locked currently is vtables (virtual function dispatch tables) and payload enums.

Witness tables are locked.  That shows which classes are connected to which protocols.

### SIL Output

Looking at output is good way to see what's happening.  First time author looked at Swift source there was a giant "FIX ME."

Name-mangling is combining proterties like namespace and class into something unique.  Which is why we don't have to worry about adding namespaces to ObjC stuff.

Struct Findings:

* stack space is explicitly added for self

* stores appear to be atomic, which is weird because we're told to make stores non-atomic

### Struct LLVM IR

The original types get carried over, along with some padding.

What if we make them private?  Will data layouts change?
