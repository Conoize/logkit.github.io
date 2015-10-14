{% case include.family %}

{% when 1.0 or 1.1 %}


The following initializers are available for `LXLogFileEndpoint`:

{% highlight swift %}
init?(fileURL: minimumLogLevel: dateFormatter: entryFormatter: )
{% endhighlight %}

**Parameters**

---------------------- | ------------------------------------------ | -----------
`fileURL`              | _Type:_ `NSURL?` <br> **Required**         | The file to write [Log Entries][entries] to
{% include docs/endpoints/common_params.md family=page.family %}

This [Endpoint][endpoints] writes [Log Entries][entries] to the file specified by `fileURL`. The `fileURL` argument is required. If the specified file cannot be opened, or if the URL evaluates to `nil`, the initializer may fail.

**Returns** an initialized File Endpoint instance if successful, or `nil` if the file cannot be opened.

***

{% highlight swift %}
convenience init?(minLogLevel: dateFormatter: entryFormatter: )
{% endhighlight %}

**Parameters**

---------------------- | ------------------------------------------ | -----------
{% include docs/endpoints/common_params.md family=page.family %}

This [Endpoint][endpoints] writes [Log Entries][entries] to the default log file, specified as `{AppSupport}/{bundleID}/logs/log.txt` where `{AppSupport}` is the system-determined Application Support directory, and `{bundleID}` is the host application's `bundleIdentifier` string. If the specified file cannot be opened, or if the URL evaluates to `nil`, the initializer may fail.

**Returns** an initialized File Endpoint instance if successful, or `nil` if the file cannot be opened.


{% else %}


The following initializers are available for `LXFileEndpoint`:

{% highlight swift %}
init?(fileURL: shouldAppend: minimumPriorityLevel: dateFormatter: entryFormatter: )
{% endhighlight %}

**Parameters**

---------------------- | ------------------------------------------ | -----------
`fileURL`              | _Type:_ `NSURL?` <br> _Default:_ see below | The file to write [Log Entries][entries] to
`shouldAppend`         | _Type:_ `Bool` <br> _Default:_ `true`      | Indicates whether the [Endpoint][endpoints] should continue appending [Log Entries][entries] to the end of the file, or clear it and start at the beginning
{% include docs/endpoints/common_params.md family=page.family %}

This [Endpoint][endpoints] writes [Log Entries][entries] to the file specified by `fileURL`. If the specified file cannot be opened, or if the URL evaluates to `nil`, the initializer may fail.

If omitted, the URL defaults to `{AppSupport}/{bundleID}/logs/log.txt`, where `{AppSupport}` is the system-determined Application Support directory, and `{bundleID}` is the host application's `bundleIdentifier` string.

**Returns** an initialized File Endpoint instance if successful, or `nil` if the file cannot be opened.


{% endcase %}
