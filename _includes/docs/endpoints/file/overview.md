{% case include.family %}

{% when 2.0 %}
The `LXFileEndpoint` writes [Log Entries][entries] to a specified file.

{% include docs/endpoints/synchronicity.md family=page.family endpoint_type="File" %}

{% endcase %}
