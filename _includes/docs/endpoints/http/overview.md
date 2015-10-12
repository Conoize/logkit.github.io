{% case include.family %}

{% when 2.0 %}
The `LXHTTPEndpoint` uploads [Log Entries][entries] to an HTTP service in plaintext format.

Upload and retry management are handled automatically by this [Endpoint][endpoints]. Log Entries that do not successfully upload will be queued for another attempt at a later time. Entries are persisted to disk until they are successfully uploaded, including between application runs, so that extended network outages do not cause Log Entries to be lost.

This Endpoint attempts to deliver Log Entries in the order in which they were generated, but because network performance is very unpredictable, this is not guaranteed. It is recommended that developers include a timestamp in this Endpoint’s `entryFormatter` to facilitate sorting at the HTTP service. The default `entryFormatter` includes the [`dateTime` property][entries]. Developers are also encouraged to investigate the [`timestamp` property][entries].

{% include docs/endpoints/synchronicity.md family=page.family endpoint_type="HTTP" %}

{% endcase %}
