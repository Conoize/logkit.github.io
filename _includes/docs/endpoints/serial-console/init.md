{% case include.family %}

{% when 1.0 or 1.1 %}


The following initializers are available for `LXLogSerialConsoleEndpoint`:

{% highlight swift %}
init(minimumLogLevel: dateFormatter: entryFormatter: )
{% endhighlight %}

**Parameters**

---------------------- | ------------------------------------- | -----------
{% include docs/endpoints/common_params.md family=page.family %}

**Returns** an initialized Serial Console Endpoint instance.


{% endcase %}
