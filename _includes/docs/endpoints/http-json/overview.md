{% case include.family %}

{% when 1.0 or 1.1 %}


The `LXLogHTTPJSONEndpoint` uploads [Log Entries][entries] to an HTTP service. The Entries are serialized in [JSON][json] format.

Upload and retry management are handled automatically by this [Endpoint][endpoints]. Log Entries that do not successfully upload will be queued for another attempt at a later time. However, pending uploads are not persisted between application runs.

This [Endpoint][endpoints] attempts to deliver Log Entries in the order in which they were generated, but because network performance is very unpredictable, this is not guaranteed.

{% include docs/endpoints/synchronicity.md family=page.family endpoint_type="HTTP JSON" %}


{% else %}


The `LXHTTPJSONEndpoint` uploads [Log Entries][entries] to an HTTP service. The Entries are serialized in [JSON][json] format.

Upload and retry management are handled automatically by this [Endpoint][endpoints]. Log Entries that do not successfully upload will be queued for another attempt at a later time. Entries are persisted to disk until they are successfully uploaded, including between application runs, so that extended network outages do not cause Log Entries to be lost.

This [Endpoint][endpoints] attempts to deliver Log Entries in the order in which they were generated, but because network performance is very unpredictable, this is not guaranteed. The JSON HTTP Endpoint may attempt to improve network performance by uploading multiple Log Entries in the same request.

{% include docs/endpoints/synchronicity.md family=page.family endpoint_type="HTTP JSON" %}


{% endcase %}
