## Building an A/B Testing Framework
### That works for developers

* Session: https://360idev.com/sessions/building-an-a-b-testing-framework-that-works-for-developers/

### Author

Jenny Chang Ho
Senior iOS Engineer @ GRUBHUB
Twitter: @TipTopGS

Started as SWE at Google, consulted with IBM, TL/mobile at Royal Bank of Canada

### A/B Testing is

**Feature Flagging**
* Workflows, designs
* Controlling rollouts of features

Sometimes we release, sometimes we iterate, sometimes we shut it down.

Innovate while minimizing risks.

We can test anything that's measurable.  For instance, "increase the number of orders."  Or just the volume of orders.  Or the conversion rate.

### Dead Code

If a feature is turned off, leaving pristine code to go unused, it increases development effort.

Devs have to build around experiments or on top of them to avoid breaking things.

QA has to test all the features and variations.

### A/B Testing is not for everyone

If you don't have a lot of users, it doesn't make sense.  You need statistical importance.  Users have qualifying selection criteria, and without enough users you may not have them.  It's also not useful in early in product development, when it'd only be blocking feature rollout.

### Experiment Examples

First losing experiment: hover-widget.

* Scheduling entry point
* Haptic feedback
* Promotions

### Keys for Success

* Objectives must be defined
* Thinking about problems from your user's perspective
* Learn from results

"Fail early, fail often, but always fail forward" -John C Maxwell

As long as we're gaining new knowledge, we're going forward.

### How to be a Good Loser

Deleting feature work hurts.  Losing never feels good even when you win.  Let's make it hurt less.

* Lesson #1
Understand what could go wrong and question assumptions.  Ask the product owners what goal they're trying to achieve.

* Lesson #2
GrubHub uses ?TapLytics?, but there's a number of A/B testing frameworks out there.  Syncing with things like Google Analytics is difficult.  Sometimes the frameworks can causes stability issues too, so test them out in your app.
