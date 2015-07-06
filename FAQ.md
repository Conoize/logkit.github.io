> Why is all the source in one file?

LogKit was meant to be easy to include in a project by just copying the source. We want to include iOS 7 in the party. Having just one file makes this much simpler to manage.  We know it's not a best practice to keep everything in one place, but at this time it feels like the right tradeoff. And the file's not exactly huge.

We may revisit this practice in a future version, when iOS 7 goes away or it otherwise makes sense.

***

> Aren't there enough logging frameworks out there? (Or, what's so special about LogKit?)

Perhaps, but when did that stop anyone? :stuck_out_tongue_winking_eye:

LogKit provides something we haven't yet seen elsewhere in Swift-based iOS/Mac logging frameworks. It's compact, extensible, includes a few nice batteries, and is documented. It's production-safe, efficient, and strives to be quick.

***

> Is there an opportunity for me to contribute?

Of course! Pull requests, issues, and discussion are welcomed! See CONTRIBUTING.md in the repo for more info.
