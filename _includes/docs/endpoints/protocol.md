{% case include.family %}

{% when 1.0 or 1.1 %}


The `LXLogEndpoint` protocol defines the following required properties:

---------------------- | --------------------- | --------------------------------
`minimumLogLevel`      | `LXLogLevel`          | The minimum [Priority Level][levels] a [Log Entry][entries] must meet to be accepted by this [Endpoint][endpoints]
`dateFormatter`        | `NSDateFormatter`     | The formatter used by this Endpoint to serialize a [Log Entry’s][entries] `dateTime` property to a string
`entryFormatter`       | `LXLogEntryFormatter` | The formatter used by this Endpoint to serialize each [Log Entry][entries] to a string

When a [Log Entry][entries] meets an Endpoint's [Priority Level][levels] requirements, and has been serialized to a string by the Endpoint's formatters, that string is passed to the Endpoint's `write:` method for output to its final destination. In the `write:` method, an Endpoint creator should print the `string` to the console, append it to a log file, or send it to whatever destination your Endpoint represents.

---------------------- | -----------------------
`write(string:String)` | Writes a serialized [Log Entry][entries] string to the final destination this Endpoint represents


{% else %}


The `LXEndpoint` protocol defines the following required properties:

---------------------- | ------------------ | --------------------------------
`minimumPriorityLevel` | `LXPriorityLevel`  | The minimum [Priority Level][levels] a [Log Entry][entries] must meet to be accepted by this [Endpoint][endpoints]
`dateFormatter`        | `LXDateFormatter`  | The formatter used by this Endpoint to serialize a [Log Entry’s][entries] `dateTime` property to a string
`entryFormatter`       | `LXEntryFormatter` | The formatter used by this Endpoint to serialize each [Log Entry][entries] to a string
`requiresNewlines`     | `Bool`             | Indicates whether this Endpoint requires a newline character appended to each serialized [Log Entry][entries] string

When a [Log Entry][entries] meets an Endpoint's [Priority Level][levels] requirements, and has been serialized to a string by the Endpoint's formatters, that string is passed to the Endpoint's `write:` method for output to its final destination. In the `write:` method, an Endpoint creator should print the `string` to the console, append it to a log file, or send it to whatever destination your Endpoint represents.

---------------------- | -----------------------
`write(string:String)` | Writes a serialized [Log Entry][entries] string to the final destination this Endpoint represents


{% endcase %}
