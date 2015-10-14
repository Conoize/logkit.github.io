{% case include.family %}

{% when 1.0 or 1.1 %}


> AppDelegate.swift

{% highlight swift %}
import Cocoa
import LogKit

let log = LXLogger(endpoints: [

    LXLogSerialConsoleEndpoint(
        dateFormatter: {
            let dateFormatter = NSDateFormatter()
            dateFormatter.dateFormat = "HH':'mm':'ss'.'SSS"
            dateFormatter.timeZone = NSTimeZone(forSecondsFromGMT: 0)
            return dateFormatter
        }(),
        entryFormatter: { entry in
            return "\(entry.dateTime) [\(entry.logLevel.uppercaseString)] \(entry.message)"
        }
    ),

    LXLogFileEndpoint(
        fileURL: (NSFileManager.defaultManager().URLsForDirectory(.DocumentDirectory, inDomains: .UserDomainMask) as? [NSURL])?.first?
            .URLByAppendingPathComponent("logs", isDirectory: true)
            .URLByAppendingPathComponent("log.txt"),
        minimumLogLevel: .Notice,
        entryFormatter: { entry in
            return "\(entry.dateTime) (\(entry.timestamp)) [\(entry.logLevel.uppercaseString)] {thread: \(entry.threadID) '\(entry.threadName)' main: \(entry.isMainThread)} \(entry.functionName) <\(entry.fileName):\(entry.lineNumber).\(entry.columnNumber)> \(entry.message)"
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

* a [Serial Console Endpoint][ep-serial-console] that asynchronously outputs [Entries][entries] of all [Priority Levels][levels], using a shortened time-only custom [date format][date-formatting] and a concise custom [Entry format][entry-formatting].
* a [File Endpoint][ep-file] that saves to a `logs` directory inside the user's Documents directory, only outputting [Entries][entries] of [Priority Level][levels] `Notice` and above, using a very detailed custom [Entry format][entry-formatting].

These are just two of several Endpoints that LogKit includes. See the [Endpoint documentation][endpoints] for other Endpoints that LogKit includes, and for information on creating your own Endpoints.


{% else %}


> AppDelegate.swift

{% highlight swift %}
import Cocoa
import LogKit

let log = LXLogger(endpoints: [

    LXConsoleEndpoint(
        synchronous: false,
        dateFormatter: LXDateFormatter.timeOnlyFormatter(),
        entryFormatter: LXEntryFormatter({ entry in
            return "\(entry.dateTime) [\(entry.level.uppercaseString)] \(entry.message)"
        })
    ),

    LXFileEndpoint(
        fileURL: (NSFileManager.defaultManager().URLsForDirectory(.DocumentDirectory, inDomains: .UserDomainMask) as? [NSURL])?.first?
            .URLByAppendingPathComponent("logs", isDirectory: true)
            .URLByAppendingPathComponent("log.txt"),
        minimumPriorityLevel: .Notice,
        entryFormatter: LXEntryFormatter({ entry in
            return "\(entry.dateTime) (\(entry.timestamp)) [\(entry.level.uppercaseString)] {thread: \(entry.threadID) '\(entry.threadName)' main: \(entry.isMainThread)} \(entry.functionName) <\(entry.fileName):\(entry.lineNumber).\(entry.columnNumber)> \(entry.message)"
        })
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

* a [Console Endpoint][ep-console] that asynchronously outputs [Entries][entries] of all [Priority Levels][levels], using a built-in shortened time-only [date format][date-formatting] and a concise custom [Entry format][entry-formatting].
* a [File Endpoint][ep-file] that saves to a `logs` directory inside the user's Documents directory, only outputting [Entries][entries] of [Priority Level][levels] `Notice` and above, using a very detailed custom [Entry format][entry-formatting].

These are just two of several Endpoints that LogKit includes. See the [Endpoint documentation][endpoints] for other Endpoints that LogKit includes, and for information on creating your own Endpoints.


{% endcase %}
