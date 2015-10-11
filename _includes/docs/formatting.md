In LogKit, [Log Entries][entries] go from `LXLogEntry` to string by using each target Endpoint's formatters. Every [Endpoint][endpoints] has its own formatters, so different Endpoints can output Entries in different formats. For example, an application using both a [Console Endpoint][ep-console] and a [File Endpoint][ep-file] could choose concise formatters for the console, and more detailed formatters for the file.

An Endpoint requires two formatters to convert each [Log Entry][entries] to a string. The Endpoint's `dateFormatter` describes how an Entry's `dateTime` property will be converted. Its `entryFormatter` describes how the Entry itself will be converted. Using the [Endpoint][endpoints]'s formatters, each `LXLogEntry` is converted to a string before the Endpoint writes it to its final destination.

Although the formatters of each Endpoint may be customized, all Endpoints include sensible defaults that will suit most developer's needs. If desired, however, a developer can choose to use another of the variety of date and Entry formatters included with LogKit, or even create and use their own.


## Date Formatters

Date formatting is handled by the `LXDateFormatter` object.

### Built-in Date Formatters

`LXDateFormatter` comes with the following built-in presets:

----------------------------- | ------------------------------------
`.standardFormatter()`        | Converts `NSDate` objects into a datetime string, using the [UTC timezone][utc] <br> _Format String:_ `yyyy-MM-dd HH:mm:ss.SSS`
`.timeOnlyFormatter()`        | Converts `NSDate` objects into a time-only string, using the [UTC timezone][utc] <br> _Format String:_ `HH:mm:ss.SSS`
`.dateOnlyFormatter()`        | Converts `NSDate` objects into a date-only string, using the [UTC timezone][utc] <br> _Format String:_ `yyyy-MM-dd`
`.ISO8601DateTimeFormatter()` | Converts `NSDate` objects into strings following the [ISO 8601 combined datetime format][iso8601], using the [UTC timezone][utc] <br> _Format String:_ `yyyy-MM-dd'T'HH:mm:ss.SSSSSSZZZZZ`

### Default Date Formatter

Unless otherwise specified by a specific [Endpoint's][endpoints] documentation, when the `dateFormatter` initialization parameter is omitted, the Endpoint will be initialized with the `.standardFormatter()` date formatter.

### Custom Date Formatters

LogKit makes creating custom date formatters easy. The `LXDateFormatter` object comes with the following initializer:

{% highlight swift %}
init(formatString: timeZone: )
{% endhighlight %}

**Parameters**

-------------- | -------------------------------------------------------- | ----------------------------------
`formatString` | _Type:_ `String` <br> **Required**                       | The date format to be used by the formatter
`timeZone`     | _Type:_ `NSTimeZone` <br> _Default:_ [UTC timezone][utc] | The time zone to use during formatting

The `formatString` parameter requires a string in the same format as Apple's [`NSDateFormatter.dateFormat` parameter][nsDateFormatter]. If omitted, the formatter will use the [UTC timezone][utc] for its `timeZone` parameter. UTC is recommended for most applications, as it makes it easy to compare datetimes from different systems in different locations.

**Returns** an initialized `LXDateFormatter` instance.

**Example:** The following creates a date formatter that outputs only the hour and minute of a [Log Entry's][entries] `dateTime` in the user's local time zone:

{% highlight swift %}
LXDateFormatter(formatString: "HH:mm", timeZone: NSTimeZone.localTimeZone())
{% endhighlight %}

> A note about precision:
>
> Although LogKit captures timestamps with microsecond precision, `LXDateFormatter` always rounds to the nearest millisecond. If your application requires microsecond precision, you should customize your Endpoint's `entryFormatter` to display each Entry's `timestamp` property, which retains microsecond precision.

### Using a Date Formatter

To use a date formatter, simply supply it to the [Endpoint][endpoints] you are initializing using the `dateFormatter` parameter. Some examples:

{% highlight swift %}
// Using a built-in date formatter:
LXConsoleEndpoint(dateFormatter: LXDateFormatter.timeOnlyFormatter())

// Using a custom date formatter:
LXConsoleEndpoint(dateFormatter: LXDateFormatter(formatString: "HH:mm:ss.SSS"))

// Omit the dateFormatter parameter to use an Endpoint's default date formatter:
LXConsoleEndpoint()
{% endhighlight %}


## Entry Formatters

[Log Entry][entries] formatting is handled by the `LXEntryFormatter` object.

### Built-in Entry Formatters

`LXEntryFormatter` includes the following built-in presets:

{% highlight swift %}
.standardFormatter()        // Converts LXLogEntry objects into strings in a standard format that contains basic debugging information
"dateTime [LEVEL] functionName <fileName:lineNumber> message"

.longFormatter()            // Converts LXLogEntry objects into strings in a long format that contains detailed debugging information
"dateTime (timestamp) [LEVEL] {thread: id name isMain} functionName <fileName:lineNumber.columnNumber> message"

.shortFormatter()           // Converts LXLogEntry objects into strings in a short format that contains minimal information
"dateTime [LEVEL] message"

.messageOnlyFormatter()     // Converts LXLogEntry objects into strings in a short format that contains only the logged message
"message"
{% endhighlight %}

### Default Entry Formatter

Unless otherwise specified by a specific [Endpoint's][endpoints] documentation, when the `entryFormatter` initialization parameter is omitted, the Endpoint will be initialized with the `.standardFormatter()` Entry formatter.

### Custom Entry Formatters

LogKit makes creating custom Entry formatters easy. The `LXEntryFormatter` object comes with the following initializer:

{% highlight swift %}
init(_: )
{% endhighlight %}
{% comment %}_ This stops the editor from turning the rest of the document purple :( {% endcomment %}

The initializer takes only one parameter - a closure of type `(LXLogEntry) -> String`. This closure must accept an `LXLogEntry` and return a `String`. The closure is free to use as many or as few of a Log Entry's properties as the developer wishes.

**Returns** an initialized `LXEntryFormatter` instance.

**Example:** The following creates a concise Entry formatter that outputs only a [Log Entry's][entries] `dateTime` and `message`:

{% highlight swift %}
LXEntryFormatter({ entry in return "\(entry.dateTime) \(entry.message)" })
{% endhighlight %}

**Example:** The following creates a detailed Entry formatter that outputs an [Entry's][entries] `timestamp`, `level`, and detailed information regarding location of the function that generated the message, as well as the `message` itself:

{% highlight swift %}
LXEntryFormatter({ entry in return "\(entry.timestamp) [\(entry.level.uppercaseString)] \(entry.functionName) <\(entry.fileName):\(entry.lineNumber).\(entry.columnNumber)> \(entry.message)" })
{% endhighlight %}

### Using an Entry Formatter

To use an Entry formatter, simply supply it to the [Endpoint][endpoints] you are initializing using the `entryFormatter` parameter. Some examples:

{% highlight swift %}
// Using a built-in Entry formatter:
LXConsoleEndpoint(entryFormatter: LXEntryFormatter.shortFormatter())

// Using a custom Entry formatter:
LXConsoleEndpoint(entryFormatter: LXEntryFormatter({ entry in return "\(entry.dateTime) \(entry.message)" }))

// Omit the entryFormatter parameter to use an Endpoint's default Entry formatter:
LXConsoleEndpoint()
{% endhighlight %}

### Customizing Entry Properties

Each [Log Entry][entries] instance contains a `userInfo` dictionary property. This dictionary's contents are set by the application developer during each [Logger method call][log-methods]. For example:

{% highlight swift %}
log.debug("Hello Internet!", ["year": "2015"])
{% endhighlight %}

Including data in `userData` can be useful in a few ways.

* The developer can supply additional properties to be included in an Entry formatter's string output.

{% highlight swift %}
let myFormatter = LXEntryFormatter({ entry in
    let year = entry.userInfo["year"] as? String ?? "unknown"
    return "\(entry.message) The year is \(year)."
})

// Hello Internet! The year is 2015.
{% endhighlight %}

* The developer can supply parameters intended to control an Entry formatter's string output.

{% highlight swift %}
let myFormatter = LXEntryFormatter({ entry in
    guard let year = entry.userInfo["year"] as? String where year == "2015" else {
        return "" // No bugs to log in 2016 and beyond!
    }
    return "\(entry.message)"
})
{% endhighlight %}

> Note: Some Endpoints (such as the included [HTTP JSON Endpoint][ep-http-json]) may automatically attempt to include any `userInfo` provided as a part of their `entryFormatter` output string.
