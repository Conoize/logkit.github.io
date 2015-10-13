{% case include.family %}

{% when 1.0 or 1.1 %}

{% else %}

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

{% endcase %}
