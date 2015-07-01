---
layout: docpage
title: Entry Formatting
---
In LogKit, log entries go from `LXLogEntry` to string by using each target [Endpoint][endpoints]'s formatters. Every Endpoint has its own formatters, so different Endpoints can output messages in different formats. For example, an application using both a [Console Endpoint][ep-console] and a [File Endpoint][ep-file] could format an entry in a short, concise way for the console, and a longer, more detailed way for the file.

An Endpoint requires two formatters: a `dateFormatter` that describes how an entry's `dateTime` will be converted, and an `entryFormatter` that describes how the entry itself will be converted. Using the [Endpoint][endpoints]'s formatters, each `LXLogEntry` is converted to a string before being sent to the Endpoint for output.

## Log Entries
Before discussing formatting, it is important to know what data is available in an `LXLogEntry`. Every log entry begins as an `LXLogEntry` containing the following properties:

Property        | Type                 | Description
--------------- | -------------------- | ------------------------------------------------------------------------------
`message`       | `String`             | The log message
`userInfo`      | `[String:AnyObject]` | Additional values to be provided to the entry formatter; always present but may be empty; see [here](#customizing-entry-properties) for using userInfo
`logLevel`      | `String`             | The name of the log entry's [Priority Level][levels]
`timestamp`     | `Double`             | The number of seconds since the [Unix epoch][epoch]
`dateTime`      | `String`             | The timestamp formatted by an Endpoint's `dateFormatter`
`functionName`  | `String`             | The name of the function from which the log entry was created
`fileName`      | `String`             | The name of the source file from which the log entry was created
`filePath`      | `String`             | The absolute path of the source file from which the log entry was created
`lineNumber`    | `Int`                | The line number within the source file from which the log entry was created
`columnNumber`  | `Int`                | The column number within the source file from which the log entry was created
`threadID`      | `String`             | The ID of the thread from which the log entry was created
`threadName`    | `String`             | The name of the thread from which the log entry was created (or an empty string if no name exists)
`isMainThread`  | `Bool`               | An indicator of whether the log entry was created on the main thread
`logKitVersion` | `String`             | The version of the LogKit framework that generated the entry

Each of these properties will be available in every `LXLogEntry` that is passed to an [Endpoint][endpoints]'s `entryFormatter`. The developer may choose to use or ignore each property when crafting a custom `LXLogEntryFormatter`.

## Default Formatters
LogKit will supply the following default formatters if no formatter is specified during [Endpoint][endpoints] initialization (unless a specific Endpoint is documented otherwise):

### Default Date Formatter
This date formatter always outputs dates using the [UTC][utc] timezone. Converts dates into strings based on the following format:

{% highlight swift %}
yyyy-MM-dd HH:mm:ss.SSS

2015-06-19 06:20:51.895
{% endhighlight %}

### Default Entry Formatter
This entry formatter converts an `LXLogEntry` into a string using the following format:

{% highlight swift %}
dateTime [LEVEL] functionName <fileName:lineNumber> message

2015-06-16 03:58:04.609 [DEBUG] applicationDidFinishLaunching <AppDelegate.swift:27> Hello Internet!
{% endhighlight %}

## Writing Formatters
At initialization time, most [Endpoints][endpoints] can optionally be supplied with a `dateFormatter` and/or an `entryFormatter`. These formatters will determine how entries are converted to strings before output. If any of the formatters is not supplied, LogKit will use an appropriate [default][default-formatting].

### Date Formatters
Date formatters are of the type `NSDateFormatter` and are [documented by Apple here][nsDateFormatter].

> A note about precision:
>
> Although LogKit captures timestamps with microsecond precision, `NSDateFormatter` always rounds to the nearest millisecond. If your application requires microsecond precision, you should customize your Endpoint's `entryFormatter` to display each entry's `timestamp` property, which retains microsecond precision.

### Entry Formatters
Entry formatters are closures of the type `LXLogEntryFormatter`, defined as:

{% highlight swift %}
typealias LXLogEntryFormatter = (entry: LXLogEntry) -> String
{% endhighlight %}

Defining an entry formatter is as simple as supplying a closure that accepts an entry and returns a string. `LXLogEntryFormatter`s receive an `LXLogEntry` and have the option to include any of its properties within the string the formatter returns.

Here are a couple examples of custom entry formatters:

{% highlight swift %}
// A short, concise formatter:
let shortFormatter: LXLogEntryFormatter = { entry in
    return "\(entry.dateTime) [\(entry.logLevel.uppercaseString)] \(entry.message)"
}

// A long, detailed formatter:
let longFormatter: LXLogEntryFormatter = { entry in
    return "\(entry.dateTime) (\(entry.timestamp)) [\(entry.logLevel.uppercaseString)] {thread: \(entry.threadID) '\(entry.threadName)' main: \(entry.isMainThread)} \(entry.functionName) <\(entry.fileName):\(entry.lineNumber).\(entry.columnNumber)> \(entry.message)"
}
{% endhighlight %}

See the [Endpoints][endpoints] documentation for details on supplying a custom formatter to an Endpoint.

#### Customizing Entry Properties

As noted [above][entries], each `LXLogEntry` instance contains a `userInfo` dictionary property. This dictionary's contents are set by the application developer during each [Logger][loggers] method call. For example:

{% highlight swift %}
log.debug("Hello Internet!", ["year": "2015"])
{% endhighlight %}

Including data in `userData` can be useful in a few ways.

* The developer can supply additional properties to be included in a formatter's string output.

{% highlight swift %}
let myFormatter: LXLogEntryFormatter = { entry in
    let year = entry.userInfo["year"] as? String ?? "unknown"
    return "\(entry.message) The year is \(year)."
}

// Hello Internet! The year is 2015.
{% endhighlight %}

* The developer can supply data intended to control a formatter's string output.

{% highlight swift %}
let myFormatter: LXLogEntryFormatter = { entry in
    if let year = entry.userInfo["year"] as? String where year == "2015" {
        return "\(entry.message)"
    } else {
        return "" // No bugs to log in 2016 and beyond!
    }
}
{% endhighlight %}

> Note: Some Endpoints (such as the included [HTTP JSON Endpoint][ep-http-json]) may automatically attempt to include any `userInfo` provided as a part of their `entryFormatter` output string.


{% include mdlinks.md %}
