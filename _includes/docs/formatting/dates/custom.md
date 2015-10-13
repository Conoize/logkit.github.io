{% case include.family %}

{% when 1.0 or 1.1 %}

Endpoint date formatting behavior can be modified by providing a custom `NSDateFormatter` instance. Please refer to [Apple's `NSDateFormatter` documentation][nsDateFormatter] for details on `NSDateFormatter` objects.

**Example:** The following creates a date formatter that outputs only the hour and minute of a [Log Entry's][entries] `dateTime` in the user's local time zone:

{% highlight swift %}
let myDateFormatter: NSDateFormatter = {
    let formatter = NSDateFormatter()
    formatter.dateFormat = "HH:mm"
    formatter.timeZone = NSTimeZone.localTimeZone()
    return formatter
}()
{% endhighlight %}

> A note about precision:
>
> Although LogKit captures timestamps with microsecond precision, `NSDateFormatter` always rounds to the nearest millisecond. If your application requires microsecond precision, you should customize your Endpoint's `entryFormatter` to display each Entry's `timestamp` property, which retains microsecond precision.

{% else %}

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

{% endcase %}
