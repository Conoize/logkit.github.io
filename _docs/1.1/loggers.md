---
layout: docpage
title: Loggers
family: 1.1
---

A Logger instance is the primary way in which an application developer interacts with LogKit. This instance is responsible for receiving log entries and distributing them to its [Endpoints][endpoints]. Generally, a Logger instance is created once, at application load time, and used throughout the life of the application. LogKit includes the `LXLogger` class which fulfills this function, and is not meant to be subclassed.

## Initializing a Logger

See the [usage documentation][usage] for practical tips on initializing a Logger. A typical Logger instance is created at the global level so that the application developer may make logging calls from all source files within a project.

Also see the [Endpoints][endpoints] documentation for information regarding the various Endpoints provided with LogKit, and their initialization options.

### Initializers

`LXLogger` contains the following initializers:

{% highlight swift %}
init(endpoints: [LXLogEndpoint?])
{% endhighlight %}

Returns an initialized and ready Logger instance populated with each of the provided [Endpoints][endpoints]. Any Endpoints that fail initialization are discarded immediately.

{% highlight swift %}
convenience init()
{% endhighlight %}

Returns an initialized and ready Logger instance. This Logger instance is populated with a standard [Console Endpoint][ep-console], configured to write entries of all [Priority Levels][levels] with the [default date and entry formatters][default-formatting].

## Logging Methods

`LXLogger` instances offer the following methods for logging within an application:

{% highlight swift %}
func debug(_ message: String)
func debug(_ message: String, userInfo: [String: AnyObject])

func info(_ message: String)
func info(_ message: String, userInfo: [String: AnyObject])

func notice(_ message: String)
func notice(_ message: String, userInfo: [String: AnyObject])

func warning(_ message: String)
func warning(_ message: String, userInfo: [String: AnyObject])

func error(_ message: String)
func error(_ message: String, userInfo: [String: AnyObject])

func critical(_ message: String)
func critical(_ message: String, userInfo: [String: AnyObject])
{% endhighlight %}

> Note: Although the `message` argument in the Logger methods above appear to accept Strings, they are actually captured as [autoclosures][autoclosures] for performance reasons. Specifically, message type is `@autoclosure(escaping) message: () -> String`. Developers should treat the `message` argument as a String, but know that their `message` will be resolved lazily, and only if at least one of the Logger's [Endpoints][endpoints] is qualified to accept the log entry.

### Defaults

A keen observer of the method signatures for each of the above logging methods may note that there are additional arguments included in each method (as seen in Xcode or [CocoaDocs][cocoadocs]). These arguments are `functionName`, `filePath`, `lineNumber`, and `columnNumber`. They are not mentioned above because they are meant to be ignored.

Each of these arguments will default to [special Swift variables][swift-specials] that automatically capture the function name, file name, line number, and column number of the code from which each of your log entries was created. Application developers should omit these arguments from their logging calls, allowing LogKit to correctly capture the scope of each call and save it in the [Log Entry][entries].

### userInfo

Each logging method above comes in two varieties: the standard method, and a method that includes a `userInfo` argument. `userInfo` provides the application developer with an opportunity to customize their logging calls. Any `userInfo` included in a logging call is captured as part of the [Log Entry][entries] and made available to each of the Logger's [Endpoints][endpoints], specifically during [Entry formatting][formatting].

[Endpoints][endpoints] may use `userInfo` in a variety of ways. In one example, a develper could provide one or more additional objects in `userInfo` that an Endpoint can later include in its [Entry Formatter][formatting] for output as part of a log entry. In another example, additional state could be included in `userInfo` that affects control flow during Entry formatting.

See [Customizing Entry Properties][user-info] for examples of using `userInfo` in your logging calls.


{% include links.md doc_version=page.family %}
