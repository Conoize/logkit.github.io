{% case include.family %}

{% when 1.0 or 1.1 or 2.0 or 2.1 %}


{% else %}


{% if include.family == 2.2 %}***New in 2.2***{% endif %}

`LXRotatingFileEndpoint` instances will post notifications before and after they rotate log files.

Before rotating files, the instance will post a `LXFileEndpointWillRotateFilesNotification` notification. The notification's `object` is the actual Endpoint instance that is rotating files. The `userInfo` dictionary contains the current and next URLs, at the `LXFileEndpointRotationCurrentURLKey` and `LXFileEndpointRotationNextURLKey` keys, respectively.

After rotating files, the instance will post a `LXFileEndpointDidRotateFilesNotification` notification. The notification's `object` is the actual Endpoint instance that is rotating files. The `userInfo` dictionary contains the current and previous URLs, at the `LXFileEndpointRotationCurrentURLKey` and `LXFileEndpointRotationPreviousURLKey` keys, respectively.

All notifications are posted to the default notification center.

> Note: Developers should **not** modify the log file currently in use by the Endpoint.

{% endcase %}
