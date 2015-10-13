{% case include.family %}

{% when 1.0 or 1.1 %}

To use an Entry formatter, simply provide it to the [Endpoint][endpoints] you are initializing using the `entryFormatter` parameter. Some examples:

{% highlight swift %}
// Using a custom Entry formatter:
LXLogConsoleEndpoint(entryFormatter: { entry in return "\(entry.dateTime) \(entry.message)" })

// Omit the entryFormatter parameter to use an Endpoint's default Entry formatter:
LXLogConsoleEndpoint()
{% endhighlight %}

{% else %}

To use an Entry formatter, simply provide it to the [Endpoint][endpoints] you are initializing using the `entryFormatter` parameter. Some examples:

{% highlight swift %}
// Using a built-in Entry formatter:
LXConsoleEndpoint(entryFormatter: LXEntryFormatter.shortFormatter())

// Using a custom Entry formatter:
LXConsoleEndpoint(entryFormatter: LXEntryFormatter({ entry in return "\(entry.dateTime) \(entry.message)" }))

// Omit the entryFormatter parameter to use an Endpoint's default Entry formatter:
LXConsoleEndpoint()
{% endhighlight %}

{% endcase %}
