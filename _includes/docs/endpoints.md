Endpoints are responsible for processing and writing [Log Entries][entries] to the destinations they represent. LogKit includes several built-in Endpoints for various logging needs, but application developers can also create their own.

Endpoints are specified when a [Logger][loggers] instance is initialized. A [Logger][loggers] instance can include several Endpoints, and each Endpoint can be configured independently.

## Included Endpoints

LogKit includes the following Endpoints ready for use:

{% case include.family %}
{% when 1.0 or 1.1 %}
* [Console Endpoint][ep-console]
* [Serial Console Endpoint][ep-serial-console]
* [File Endpoint][ep-file]
* [Dated File Endpoint][ep-dated-file]
* [HTTP Endpoint][ep-http]
* [HTTP JSON Endpoint][ep-http-json]
{% else %}
* [Console Endpoint][ep-console]
* [File Endpoint][ep-file]
* [Rotating File Endpoint][ep-rotating-file]
* [Dated File Endpoint][ep-dated-file]
* [HTTP Endpoint][ep-http]
* [HTTP JSON Endpoint][ep-http-json]
{% endcase %}

Each of these included Endpoint types has unique settings and characteristics. View each specific Endpoint's documentation to learn about initializing and using that Endpoint.

## Creating a Custom Endpoint

If the included Endpoint types do not meet your needs, LogKit makes it easy to create a custom Endpoint for use within your application. Simply define an object that conforms to LogKit's Endpoint protocol, and include it when initializing your [Logger][loggers]. The protocol defines a few properties that control which [Log Entries][entries] an Endpoint will accept and how the Entries will be [formatted][formatting], as well as a method for writing Log Entries to the destination the Endpoint represents.

### The Endpoint Protocol

{% case include.family %}

{% when 1.0 %}

The `LXLogEndpoint` protocol defines the following required properties:

---------------------- | --------------------- | --------------------------------
`minimumLogLevel`      | `LXLogLevel`          | The minimum [Priority Level][levels] a [Log Entry][entries] must meet to be accepted by this [Endpoint][endpoints]
`dateFormatter`        | `NSDateFormatter`     | The formatter used by this Endpoint to serialize a [Log Entry’s][entries] `dateTime` property to a string
`entryFormatter`       | `LXLogEntryFormatter` | The formatter used by this Endpoint to serialize each [Log Entry][entries] to a string

{% when 1.1 %}

The `LXEndpoint` protocol defines the following required properties:

---------------------- | ------------------ | --------------------------------
`minimumLogLevel`      | `LXPriorityLevel`  | The minimum [Priority Level][levels] a [Log Entry][entries] must meet to be accepted by this [Endpoint][endpoints]
`dateFormatter`        | `NSDateFormatter`  | The formatter used by this Endpoint to serialize a [Log Entry’s][entries] `dateTime` property to a string
`entryFormatter`       | `LXEntryFormatter` | The formatter used by this Endpoint to serialize each [Log Entry][entries] to a string

{% else %}

The `LXEndpoint` protocol defines the following required properties:

---------------------- | ------------------ | --------------------------------
`minimumPriorityLevel` | `LXPriorityLevel`  | The minimum [Priority Level][levels] a [Log Entry][entries] must meet to be accepted by this [Endpoint][endpoints]
`dateFormatter`        | `LXDateFormatter`  | The formatter used by this Endpoint to serialize a [Log Entry’s][entries] `dateTime` property to a string
`entryFormatter`       | `LXEntryFormatter` | The formatter used by this Endpoint to serialize each [Log Entry][entries] to a string
`requiresNewlines`     | `Bool`             | Indicates whether this Endpoint requires a newline character appended to each serialized [Log Entry][entries] string

{% endcase %}

When a [Log Entry][entries] meets an Endpoint's [Priority Level][levels] requirements and has been formatted as a string by the Endpoint's formatters, that string is passed to the Endpoint's `write:` method for output to its final destination. In the `write:` method, a developer should print the `string` to the console, append it to a log file, or send it to whatever destination your Endpoint represents.

---------------------- | -----------------------
`write(string:String)` | Writes a serialized [Log Entry][entries] string to the final destination this Endpoint represents

### Example Endpoint

Below is the code for an example custom Endpoint called `MyPrintEndpoint`. This Endpoint prints [Log Entries][entries] to Xcode's debug console.

{% case include.family %}

{% when 1.0 %}

{% highlight swift %}
class MyPrintEndpoint: LXLogEndpoint {
    var minimumLogLevel: LXLogLevel
    var dateFormatter: NSDateFormatter
    var entryFormatter: LXLogEntryFormatter

    init(minimumLogLevel: LXLogLevel, dateFormatter: NSDateFormatter, entryFormatter: LXLogEntryFormatter) {
        self.minimumLogLevel = minimumLogLevel
        self.dateFormatter = dateFormatter
        self.entryFormatter = entryFormatter
    }

    func write(string: String) {
        print(string)
    }
}
{% endhighlight %}

To use this custom Endpoint, a developer would include it when initializing their [Logger][loggers]:

{% highlight swift %}
let log = LXLogger(endpoints: [
    MyPrintEndpoint(minimumLogLevel: .All, dateFormatter: defaultDateFormatter, entryFormatter: defaultEntryFormatter)
])
{% endhighlight %}

{% when 1.1 %}

{% highlight swift %}
class MyPrintEndpoint: LXEndpoint {
    var minimumLogLevel: LXPriorityLevel
    var dateFormatter: NSDateFormatter
    var entryFormatter: LXEntryFormatter

    init(minimumLogLevel: LXPriorityLevel, dateFormatter: NSDateFormatter, entryFormatter: LXEntryFormatter) {
        self.minimumLogLevel = minimumLogLevel
        self.dateFormatter = dateFormatter
        self.entryFormatter = entryFormatter
    }

    func write(string: String) {
        print(string)
    }
}
{% endhighlight %}

To use this custom Endpoint, a developer would include it when initializing their [Logger][loggers]:

{% highlight swift %}
let log = LXLogger(endpoints: [
    MyPrintEndpoint(minimumLogLevel: .All, dateFormatter: defaultDateFormatter, entryFormatter: defaultEntryFormatter)
])
{% endhighlight %}

{% else %}

{% highlight swift %}
class MyPrintEndpoint: LXEndpoint {
    var minimumPriorityLevel: LXPriorityLevel
    var dateFormatter: LXDateFormatter
    var entryFormatter: LXEntryFormatter
    let requiresNewlines = false                // Always false for this Endpoint, because print() appends a newline automatically

    init(minimumPriorityLevel: LXPriorityLevel, dateFormatter: LXDateFormatter, entryFormatter: LXEntryFormatter) {
        self.minimumPriorityLevel = minimumPriorityLevel
        self.dateFormatter = dateFormatter
        self.entryFormatter = entryFormatter
    }

    func write(string: String) {
        print(string)
    }
}
{% endhighlight %}

To use this custom Endpoint, a developer would include it when initializing their [Logger][loggers]:

{% highlight swift %}
let log = LXLogger(endpoints: [
    MyPrintEndpoint(minimumPriorityLevel: .All, dateFormatter: LXDateFormatter.standardFormatter(), entryFormatter: LXEntryFormatter.standardFormatter())
])
{% endhighlight %}

{% endcase %}

The [Logger][loggers] instance will use its Endpoints' settings to convert each [Log Entry][entries] to a string, before asking the Endpoint to `write` it.
