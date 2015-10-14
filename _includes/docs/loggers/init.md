{% case include.family %}

{% when 1.0 or 1.1 %}


See the [usage documentation][usage] for practical tips on initializing a Logger. A typical Logger instance is created at the global level so that the application developer may make logging calls from all source files within a project.

Also see the [Endpoints][endpoints] documentation for information regarding the various Endpoints provided with LogKit, and their initialization options.

The following initializers are available for `LXLogger`:

{% highlight swift %}
init(endpoints: [LXLogEndpoint?])
{% endhighlight %}

**Returns** an initialized and ready Logger instance populated with each of the provided [Endpoints][endpoints]. Any Endpoints that fail initialization are discarded immediately.

***

{% highlight swift %}
convenience init()
{% endhighlight %}

**Returns** an initialized and ready Logger instance. This Logger instance is populated with a standard [Console Endpoint][ep-console], configured to write [Entries][entries] of all [Priority Levels][levels] with the [default date][default-date-formatting] and [Entry formatters][default-entry-formatting].


{% else %}


See the [usage documentation][usage] for practical tips on initializing a Logger. A typical Logger instance is created at the global level so that the application developer may make logging calls from all source files within a project.

Also see the [Endpoints][endpoints] documentation for information regarding the various Endpoints provided with LogKit, and their initialization options.

The following initializers are available for `LXLogger`:

{% highlight swift %}
init(endpoints: [LXEndpoint?])
{% endhighlight %}

**Returns** an initialized and ready Logger instance populated with each of the provided [Endpoints][endpoints]. Any Endpoints that fail initialization are discarded immediately.

***

{% highlight swift %}
convenience init()
{% endhighlight %}

**Returns** an initialized and ready Logger instance. This Logger instance is populated with a standard [Console Endpoint][ep-console], configured to write [Entries][entries] of all [Priority Levels][levels] with the [default date][default-date-formatting] and [Entry formatters][default-entry-formatting].


{% endcase %}
