{% case include.family %}

{% when 1.0 or 1.1 %}

Unless otherwise specified by a specific [Endpoint's][endpoints] documentation, when the `dateFormatter` initialization parameter is omitted, the Endpoint will be initialized with the default date formatter. This formatter uses the following format:

{% highlight swift %}
yyyy-MM-dd HH:mm:ss.SSS

2015-06-19 06:20:51.895
{% endhighlight %}

{% else %}

Unless otherwise specified by a specific [Endpoint's][endpoints] documentation, when the `dateFormatter` initialization parameter is omitted, the Endpoint will be initialized with the `.standardFormatter()` date formatter.

{% endcase %}
