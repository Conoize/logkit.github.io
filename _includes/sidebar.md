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
* [Log Entries][entries]
* [Priority Levels][levels]
* [Entry Formatting][formatting]
{% else %}
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
* [Log Entries][entries]
* [Priority Levels][levels]
* [Entry Formatting][formatting]
{% endcase %}

***
{% case include.version %}{% when 1.0 or 1.1 %}
{% else %}* [Migrating][migration]{% endcase %}
* [ChangeLog][changelog]
* [CocoaDocs][cocoadocs]


{% include links.md doc_version=include.version %}
