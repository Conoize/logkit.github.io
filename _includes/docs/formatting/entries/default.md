{% case include.family %}

{% when 1.0 or 1.1 %}

Unless otherwise specified by a specific [Endpoint's][endpoints] documentation, when the `entryFormatter` initialization parameter is omitted, the Endpoint will be initialized with the default Entry formatter. This formatter uses the following format:

{% highlight swift %}
dateTime [LEVEL] functionName <fileName:lineNumber> message

2015-06-16 03:58:04.609 [DEBUG] applicationDidFinishLaunching <AppDelegate.swift:27> Hello Internet!
{% endhighlight %}

{% else %}

Unless otherwise specified by a specific [Endpoint's][endpoints] documentation, when the `entryFormatter` initialization parameter is omitted, the Endpoint will be initialized with the `.standardFormatter()` Entry formatter.

{% endcase %}
