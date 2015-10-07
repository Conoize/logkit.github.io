# {{ include.version }} Docs

{% case include.version %}
{% when 1.0 or 1.1 %}
* [Installation][installation]
* [Usage][usage]
* [Loggers][loggers]
* [Endpoints][endpoints]
  * [Console][ep-console]
  * [Serial Console][ep-serial-console]
  * [File][ep-file]
  * [Dated File][ep-dated-file]
  * [HTTP][ep-http]
  * [HTTP JSON][ep-http-json]
* [Priority Levels][levels]
* [Entry Formatting][formatting]
{% when 2.0 %}
* [Installation][installation]
* [Usage][usage]
* [Loggers][loggers]
* [Endpoints][endpoints]
  * [Console][ep-console]
  * [File][ep-file]
  * [Rotating File][ep-rotating-file]
  * [Dated File][ep-dated-file]
  * [HTTP][ep-http]
  * [HTTP JSON][ep-http-json]
* [Priority Levels][levels]
* [Entry Formatting][formatting]
{% else %}

{% endcase %}

{% include links.md doc_version=include.version %}
