{% case include.family %}

{% when 1.0 or 1.1 %}


The `LXLogDatedFileEndpoint` writes [Log Entries][entries] to a selected file. At initialization time, the specified file’s name is prepended with a datestamp.

{% include docs/endpoints/synchronicity.md family=page.family endpoint_type="Dated File" %}


{% else %}


The `LXDatedFileEndpoint` writes [Log Entries][entries] to a selected file, which changes a daily. Developers can specify a base URL for the log files, and the [Endpoint][endpoints] will prepend the current datestamp to each file's name. At each midnight [UTC][utc], the Endpoint will create a new dated file for that day's logging.

{% include docs/endpoints/synchronicity.md family=page.family endpoint_type="Dated File" %}


{% endcase %}
