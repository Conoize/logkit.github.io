{% case include.family %}

{% when 2.0 %}
The `LXDatedFileEndpoint` writes Log Entries to a selected file, which changes a daily. Developers can specify a base URL for the log files, and the [Endpoint][endpoints] will prepend the current datestamp to each file's name. At each midnight [UTC][utc], the Endpoint will create a new dated file for that day's logging.
{% endcase %}
