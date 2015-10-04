---
layout: docpage
title: Usage
family: 1.1
---

## Quick Start

LogKit makes it easy to get started logging!

1. [Install LogKit][installation]
2. `import LogKit`
3. Create a [Logger][loggers]

> Note: If you installed LogKit by including its source directly within your project, there is no need to `import LogKit` (in fact, you will not be able to). Skip that step and just create a Logger.

To get started right away, install LogKit and follow the Simple Example code below. Later, you can add more [Endpoints][endpoints] by simply modifying your [Logger's][loggers] initialization. All of your logging calls will begin outputting to the new Endpoints!

### Simple Example (in iOS)

> AppDelegate.swift

{% highlight swift linenos %}
import UIKit
import LogKit

let log = LXLogger()

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate, UISplitViewControllerDelegate {
    // ...

    func application(application: UIApplication, didFinishLaunchingWithOptions launchOptions: [NSObject : AnyObject]?) -> Bool {

        log.debug("Hello Internet!")

        return true
    }
}
{% endhighlight %}

This simple example initializes a [Logger][loggers] with a standard [Console Endpoint][ep-console]. Lines 2, 4, and 12 contain the relevant code for quickly getting LogKit set up.

Because the Logger instance `log` is created as a global, you may now make logging calls from any of your project's source files.

## Advanced Usage

The basics of LogKit don't change, but its real power comes from using [Endpoints][endpoints] other than the console. LogKit allows you to write log entries to as many Endpoints as desired. Each of these Endpoints can be customized to log in different [formats][formatting], or set to accept different [Priority Levels][levels].

### Complex Example (in OS X) with Multiple Endpoints

> AppDelegate.swift

{% highlight swift %}
import Cocoa
import LogKit

let log = LXLogger(endpoints: [

    LXSerialConsoleEndpoint(
        dateFormatter: {
            let dateFormatter = NSDateFormatter()
            dateFormatter.dateFormat = "HH':'mm':'ss'.'SSS"
            dateFormatter.timeZone = NSTimeZone(forSecondsFromGMT: 0)
            return dateFormatter
        }(),
        entryFormatter: { entry in
            return "\(entry.dateTime) [\(entry.level.uppercaseString)] \(entry.message)"
        }
    ),

    LXFileEndpoint(
        fileURL: (NSFileManager.defaultManager().URLsForDirectory(.DocumentDirectory, inDomains: .UserDomainMask) as? [NSURL])?.first?
            .URLByAppendingPathComponent("logs", isDirectory: true)
            .URLByAppendingPathComponent("log.txt"),
        minimumLogLevel: .Notice,
        entryFormatter: { entry in
            return "\(entry.dateTime) (\(entry.timestamp)) [\(entry.level.uppercaseString)] {thread: \(entry.threadID) '\(entry.threadName)' main: \(entry.isMainThread)} \(entry.functionName) <\(entry.fileName):\(entry.lineNumber).\(entry.columnNumber)> \(entry.message)"
        }
    ),

])

@NSApplicationMain
class AppDelegate: NSObject, NSApplicationDelegate {
    // ...

    func applicationDidFinishLaunching(aNotification: NSNotification) {

        log.info("Hello, Internet...")
        log.notice("... do you hear me?")

    }
}
{% endhighlight %}

This complex example initializes a [Logger][loggers] with several [Endpoints][endpoints]:

* a [Serial Console Endpoint][ep-serial-console] that outputs messages of all [Levels][levels], using a shortened time-only date format and a concise entry format.
* a [File Endpoint][ep-file] that saves to a `logs` directory inside the User's Documents directory, only outputting entries of [Level][levels] `Notice` and above, using the default date format and a very detailed entry format.

These are just two of several Endpoints that LogKit includes. See the [Endpoints documentation][endpoints] for other Endpoints that LogKit includes, and for information on creating your own Endpoints.


{% include links.md doc_version=page.family %}
