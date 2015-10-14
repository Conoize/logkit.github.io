{% case include.family %}

{% else %}


`LXLogger` instances offer the following methods for logging within an application:

{% highlight swift %}
func debug(_ message: String, userInfo: [String: AnyObject] = [:])

func info(_ message: String, userInfo: [String: AnyObject] = [:])

func notice(_ message: String, userInfo: [String: AnyObject] = [:])

func warning(_ message: String, userInfo: [String: AnyObject] = [:])

func error(_ message: String, userInfo: [String: AnyObject] = [:])

func critical(_ message: String, userInfo: [String: AnyObject] = [:])
{% endhighlight %}

In each case, the `userInfo` parameter may be omitted. If omitted, `userInfo` will default to an empty dictionary.

> Note: Although the `message` parameter in the Logger methods above appear to accept Strings, they are actually captured as [autoclosures][autoclosures] for performance reasons. Specifically, message type is `@autoclosure(escaping) message: () -> String`. Developers should treat the `message` parameter as a String, but be aware that their `message` will be resolved lazily, and only if the [Log Entry][entries] meets at least one [Endpoint's][endpoints] minimum [Priority Level][levels] requirements.


{% endcase %}
