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
