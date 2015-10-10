{% case include.family %}

{% when 2.0 %}
The `LXRotatingFileEndpoint` writes [Log Entries][entries] to a rotating group of files. Developers can specify the number of files to use, and the maximum size a file can reach.

At initialization time, the specified URL will be used to create a group of files, each prepended with an index number. Before writing each Entry, the [Endpoint][endpoints] will check if the current file has reached its maximum size, and if so, will rotate to the next file before writing. Each time the Endpoint rotates, it clears the newly selected file and starts from its beginning.

{% include docs/endpoints/synchronicity.md family=page.family endpoint_type="Rotating File" %}

{% endcase %}
