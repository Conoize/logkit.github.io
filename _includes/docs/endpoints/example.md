{% case include.family %}

{% when 1.0 or 1.1 %}


Below is the code for an example custom Endpoint called `MyPrintEndpoint`. This Endpoint prints [Log Entries][entries] to Xcode's debug console.

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
        println(string)
    }
}
{% endhighlight %}

To use this custom Endpoint, a developer would include it when initializing their [Logger][loggers]:

{% highlight swift %}
let log = LXLogger(endpoints: [
    MyPrintEndpoint(minimumLogLevel: .All, dateFormatter: defaultDateFormatter, entryFormatter: defaultEntryFormatter)
])
{% endhighlight %}

The [Logger][loggers] instance will use its Endpoints' settings to convert each [Log Entry][entries] to a string, before asking the Endpoint to `write` it.


{% else %}


Below is the code for an example custom Endpoint called `MyPrintEndpoint`. This Endpoint prints [Log Entries][entries] to Xcode's debug console.

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

The [Logger][loggers] instance will use its Endpoints' settings to convert each [Log Entry][entries] to a string, before asking the Endpoint to `write` it.


{% endcase %}
