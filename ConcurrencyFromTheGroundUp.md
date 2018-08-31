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
2. Thinking in terms of tasks
3. Protecting resources

### Concurrency and Structure
* Concurrency vs Parallelism
    * "*Concurrency* is the composition of independently executing processes." (- Rob Pike)
    * "*Parallelism* is the simultaneous execution of computations."
    * "*Concurrency* is about ** *dealing* ** with lots of things at once. *Parallelism* is about ** *doing* ** lots of things at once."
* Order? Shared state? Mutable state?

### Tasks and Threads

We use threads to model our tasks.

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

We use locks to model our access to resources.

* Locks are all about protecting access to code.
* `let lock = NSLock()`
    * A lock is is like the conch shell that somebody has to be holding to talk. It's a token that means only one thing can access a property at at time.

There are two different uses for locks:
* Locks as signals (wait until A is done to start B)
* Locks as mutual exclusion (protect access to shared state from multiple threads)

// Sorry, I got really behind the presenter at this point. Notes end here.
