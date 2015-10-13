{% case include.family %}

{% when 1.0 or 1.1 %}

To use a date formatter, simply provide it to the [Endpoint][endpoints] you are initializing using the `dateFormatter` parameter. Some examples:

{% highlight swift %}
// Using a custom date formatter:
LXLogConsoleEndpoint(
    dateFormatter: {
        let formatter = NSDateFormatter()
        formatter.dateFormat = "HH:mm"
        formatter.timeZone = NSTimeZone.localTimeZone()
        return formatter
    }()
)

// Omit the dateFormatter parameter to use an Endpoint's default date formatter:
LXLogConsoleEndpoint()
{% endhighlight %}

{% else %}

To use a date formatter, simply supply it to the [Endpoint][endpoints] you are initializing using the `dateFormatter` parameter. Some examples:

{% highlight swift %}
// Using a built-in date formatter:
LXConsoleEndpoint(dateFormatter: LXDateFormatter.timeOnlyFormatter())

// Using a custom date formatter:
LXConsoleEndpoint(dateFormatter: LXDateFormatter(formatString: "HH:mm:ss.SSS"))

// Omit the dateFormatter parameter to use an Endpoint's default date formatter:
LXConsoleEndpoint()
{% endhighlight %}

{% endcase %}
