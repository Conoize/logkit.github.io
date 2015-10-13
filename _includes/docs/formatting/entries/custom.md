{% case include.family %}

{% when 1.0 or 1.1 %}


LogKit makes creating custom Entry formatters easy. The `LXLogEntryFormatter` closure is defined as:

{% highlight swift %}
typealias LXLogEntryFormatter = (entry: LXLogEntry) -> String
{% endhighlight %}

Defining an entry formatter is as simple as providing a closure that accepts a [Log Entry][entries] and returns a string.

**Example:** The following creates a concise Entry formatter that outputs only a [Log Entry's][entries] `dateTime` and `message`:

{% highlight swift %}
let shortFormatter: LXLogEntryFormatter = { entry in return "\(entry.dateTime) \(entry.message)" }
{% endhighlight %}

**Example:** The following creates a detailed Entry formatter that outputs an [Entry's][entries] `timestamp`, `logLevel`, and detailed information regarding location of the function that generated the message, as well as the `message` itself:

{% highlight swift %}
let logFormatter: LXLogEntryFormatter = { entry in
    return "\(entry.timestamp) [\(entry.logLevel.uppercaseString)] \(entry.functionName) <\(entry.fileName):\(entry.lineNumber).\(entry.columnNumber)> \(entry.message)"
}
{% endhighlight %}


{% else %}


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


{% endcase %}
