# Concurrency From the Ground Up
**Greg Heo** -
[*@gregheo*](https://twitter.com/gregheo) -
from Swift Unboxed

#### Why?
* Because we want:
    1. Programs that seem faster to the user.
    2. Programs that are easy to understand for the programmer.

#### How?
1. Structuring our programs better
2. Thinking in terms of Tasks
3. Protecting Resources

### Concurrency and Structure
* Concurrency vs Parallelism
    * "*Concurrency* is the composition of independently executing processes."
    * "*Parallelism* is the simultaneous execution of computations."
    * "*Concurrency* is about ** *dealing* ** with lots of things at once. *Parallelism* is about ** *doing* ** lots of things at once."
* Order? Shared state? Mutable state?

### Tasks and Threads
```Swift
var tProcessData: pthread_t?
pthread_create(&tProcessData, nil, processData, nil)
pthread_join(tProcessData!, nil) //This will block until the work is complete.
```
* The concept is:
    1. Create a thread
    2. Run some code
    3. Wait for it to complete

### Locks and Resources
* Locks are all about protecting access to code.
* `let lock = NSLock()`
    * A lock is is like the conch shell that somebody has to be holding to talk. It's a token that means only one thing can access a property at at time.
* Locks as signals vs locks as mutual exclusion

// Sorry, I got really behind the presenter at this point. Notes end here.
