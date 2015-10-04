---
layout: docpage
title: Priority Levels
family: 1.1
---

LogKit supports a variety of log entry Priority Levels, as defined in the `LXLogLevel` enumeration. The supported Levels are:

Level      | Priority | Suggested Use
---------- | -------- | ------------------------------------------------------------------------
`All`      |          | Special value that includes all Levels
`Debug`    | Low      | Programmer debugging
`Info`     |          | Programmer informational
`Notice`   |          | General notice
`Warning`  |          | An event that may affect user experience, if not corrected, has occurred
`Error`    |          | An event that will definitely affect user experience has occurred
`Critical` | High     | An event that may crash the application has occurred
`None`     |          | Special value that excludes all Levels

When using a [Logger][loggers], the Level for each log entry will be determined by the Logger method called to create the entry. Each of a Logger's [Endpoints][endpoints] may individually set a minimum accepted Level, and thus some log entries may be excluded from reaching specific Endpoints.

> The Levels `All` and `None` are special values for including and excluding all other Levels, respectively. `All` and `None` are not available as [Logger methods][log-methods].

{% include links.md doc_version=page.family %}
