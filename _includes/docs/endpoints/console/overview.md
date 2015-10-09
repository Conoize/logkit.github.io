{% case include.family %}

{% when 2.0 %}
The `LXConsoleEndpoint` writes log entries to the console (stdout).

> The Console Endpoint is safe to be used in environments featuring concurrency, and may or may not perform work asynchronously depending on its initialization parameters. Please see below.

{% endcase %}
