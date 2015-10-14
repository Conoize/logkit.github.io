{% case include.family %}

{% else %}


The `LXLogSerialConsoleEndpoint` writes [Log Entries][entries] to the console (`stdout`) asynchronously.

{% include docs/endpoints/synchronicity.md family=page.family endpoint_type="Serial Console" %}


{% endcase %}
