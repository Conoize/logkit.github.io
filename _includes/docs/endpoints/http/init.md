{% case include.family %}

{% when 1.0 or 1.1 %}


The following initializers are available for `LXLogHTTPEndpoint`:

{% highlight swift %}
init(URL: HTTPMethod: successCodes: sessionConfiguration: minimumLogLevel: dateFormatter: entryFormatter: )
{% endhighlight %}

**Parameters**

---------------------- | ---------------------------------- | -----------
`URL`                  | _Type:_ `NSURL` <br> **Required**  | The URL to upload Log Entries to
`HTTPMethod`           | _Type:_ `String` <br> **Required** | The HTTP request method to be used when uploading Log Entries
`successCodes`         | _Type:_ `Set<Int>` <br> _Default:_ `{200, 201, 202, 204}` | The set of [HTTP status codes][statusCodes] the server might respond with to indicate a successful upload
`sessionConfiguration` | _Type:_ `NSURLSessionConfiguration` <br> _Default:_ `.defaultSessionConfiguration()` | The configuration to be used when initializing this [Endpoint][endpoints]'s URL session
{% include docs/endpoints/common_params.md family=page.family %}

This Endpoint will upload Log Entries to the specified `URL` using the specified `HTTPMethod`. The Endpoint will create a basic `text/plain` [`NSURLRequest`][nsURLRequest] object to be used for all [Log Entry][entries] uploads. Developers that require more flexibility in configuring upload requests may investigate supplying a customized [`NSURLSessionConfiguration`][nsURLSessionConfig].

**Returns** an initialized HTTP Endpoint instance.


{% else %}


The following initializers are available for `LXHTTPEndpoint`:

{% highlight swift %}
init(request: successCodes: sessionConfiguration: minimumPriorityLevel: dateFormatter: entryFormatter: )
{% endhighlight %}

**Parameters**

---------------------- | ---------------------------------------- | -----------
`request`              | _Type:_ `NSURLRequest` <br> **Required** | The request that will be used when submitting uploads
`successCodes`         | _Type:_ `Set<Int>` <br> _Default:_ `{200, 201, 202, 204}` | The set of [HTTP status codes][statusCodes] the server might respond with to indicate a successful upload
`sessionConfiguration` | _Type:_ `NSURLSessionConfiguration` <br> _Default:_ `.defaultSessionConfiguration()` | The configuration to be used when initializing this [Endpoint][endpoints]'s URL session
{% include docs/endpoints/common_params.md family=page.family %}

Developers must supply an [`NSURLRequest`][nsURLRequest] when initializing this [Endpoint][endpoints]. This request object will be copied and used to upload each [Log Entry][entries] to the HTTP service.

**Returns** an initialized HTTP Endpoint instance.

***

{% highlight swift %}
convenience init(URL: HTTPMethod: successCodes: sessionConfiguration: minimumPriorityLevel: dateFormatter: entryFormatter: )
{% endhighlight %}

**Parameters**

---------------------- | ---------------------------------- | -----------
`URL`                  | _Type:_ `NSURL` <br> **Required**  | The URL to upload Log Entries to
`HTTPMethod`           | _Type:_ `String` <br> **Required** | The HTTP request method to be used when uploading Log Entries
`successCodes`         | _Type:_ `Set<Int>` <br> _Default:_ `{200, 201, 202, 204}` | The set of [HTTP status codes][statusCodes] the server might respond with to indicate a successful upload
`sessionConfiguration` | _Type:_ `NSURLSessionConfiguration` <br> _Default:_ `.defaultSessionConfiguration()` | The configuration to be used when initializing this [Endpoint][endpoints]'s URL session
{% include docs/endpoints/common_params.md family=page.family %}

This convenience initializer allows developers to supply a URL and request method when initializing this [Endpoint][endpoints]. The Endpoint will create a basic `text/plain` [`NSURLRequest`][nsURLRequest] object to be used for all [Log Entry][entries] uploads. Developers that require more flexibility in configuring upload requests should use the designated initializer above, or determine whether supplying a customized [`NSURLSessionConfiguration`][nsURLSessionConfig] meets their needs.

**Returns** an initialized HTTP Endpoint instance.


{% endcase %}
