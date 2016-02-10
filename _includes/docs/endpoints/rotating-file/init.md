{% case include.family %}

{% when 1.0 or 1.1 %}


{% else %}


The following initializers are available for `LXRotatingFileEndpoint`:

{% highlight swift %}
init?(baseURL: numberOfFiles: maxFileSizeKiB: minimumPriorityLevel: dateFormatter: entryFormatter: )
{% endhighlight %}

**Parameters**

---------------------- | ------------------------------------ | -----------
`baseURL`        | _Type:_ `NSURL?` <br> _Default:_ see below | The URL used to build the rotating file set's file URLs; see description below
`numberOfFiles`  | _Type:_ `UInt` <br> _Default:_ `5`         | The number of files to be used in the rotation
`maxFileSizeKiB` | _Type:_ `UInt` <br> _Default:_ `1024`      | The maximum file size of each file in the rotation, specified in kilobytes
{% include docs/endpoints/common_params.md family=page.family %}

This [Endpoint][endpoints] writes [Log Entries][entries] to a set of files specified by `baseURL`, with each file's name automatically prepended with an index number indicating its place in the rotation. If the specified file cannot be opened, or if the index-prepended URL evaluates to `nil`, the initializer may fail.

If omitted, the URL defaults to `{AppSupport}/{bundleID}/logs/{number}_log.txt`, where `{AppSupport}` is the system-determined Application Support directory, `{bundleID}` is the host application's `bundleIdentifier` string, and `{number}` is the index of the currently selected file.

As an example, if an `LXRotatingFileEndpoint` is initialized with its default parameter values, it will create a set of files in `Application Support/{bundleID}/logs/` named `1_log.txt`, `2_log.txt`, `3_log.txt`, `4_log.txt`, and `5_log.txt`.

**Returns** an initialized Rotating File Endpoint instance if successful, or `nil` if the file cannot be accessed.


{% endcase %}
