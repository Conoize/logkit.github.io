{% case include.family %}

{% else %}


Each time a [Logger method][log-methods] is called, LogKit automatically gathers a variety of details regarding the message, its source, the runtime environment, and the host device. These details are collected into a Log Entry instance.

Developers creating [custom Entry formatters][custom-entry-formatting] may choose to include any number of the available properties in their serialization format.


{% endcase %}
