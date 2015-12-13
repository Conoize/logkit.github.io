{% case include.family %}

{% when 1.0 or 1.1 %}


The `LXLogConsoleEndpoint` writes [Log Entries][entries] to the console (`stdout`).

All Entries sent to this [Endpoint][endpoints] are written synchronously. The application will wait for each [Log Entry][entries] to be printed to the console before continuing execution. This behavior is very helpful when debugging, but may reduce performance compared to the [Serial Console][ep-serial-console], which uses asynchronous behavior.


{% when 2.0 %}


The `LXConsoleEndpoint` writes [Log Entries][entries] to the console (`stdout`).

> The Console Endpoint is safe to be used in environments featuring concurrency, and may or may not perform work asynchronously depending on its initialization parameters. Please see below.


{% else %}


The `LXConsoleEndpoint` writes [Log Entries][entries] to the console (`stderr`).

> The Console Endpoint is safe to be used in environments featuring concurrency, and may or may not perform work asynchronously depending on its initialization parameters. Please see below.


{% endcase %}
