{% case include.family %}

{% when 1.0 or 1.1 %}


The `LXLogFileEndpoint` writes [Log Entries][entries] to a specified file.

{% include docs/endpoints/synchronicity.md family=page.family endpoint_type="File" %}


{% else %}


The `LXFileEndpoint` writes [Log Entries][entries] to a specified file.

{% include docs/endpoints/synchronicity.md family=page.family endpoint_type="File" %}


{% endcase %}
