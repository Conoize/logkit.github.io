---
layout: page
title: About
---

{% include summary.md %}

## Design

LogKit was designed with a few goals in mind:

### Simplicity

LogKit comes ready to get you logging to the console in one line of code. With LogKit's no-argument convenience initializer, you can skip the "where?" and "how?" questions for now, and come back to them later.

When you do want to begin logging to a file, or uploading log entries to an HTTP service, you'll simply add more [Endpoints][endpoints] to your [Logger][loggers]. All of your existing log calls will begin using the new Endpoints the next time you build your app.

LogKit comes with a variety of ready-built [Endpoints][endpoints] for logging to the [console][ep-console], [files][ep-file], or [HTTP services][ep-http], with options like [thread-friendly console output][ep-serial-console] (no jumbles!), [dated filenames][ep-dated-file], and [JSON output to HTTP][ep-http-json].

### Efficiency

LogKit is written with efficiency in mind. Where appropriate, LogKit uses Grand Central Dispatch to do the heavy lifting. However, the LogKit framework is not completely asynchronous - it does not always make sense for your log messages to (not) show up until after your app has crashed. LogKit attempts to find a balance between timely logging and vacating the main thread. LogKit also bails out early if none of its [Endpoints][endpoints] care about a particular entry.

### Safety

Your logging library should not crash your (shipping) application. LogKit was designed to silently drop [Endpoints][endpoints] and logging calls that fail in shipping builds. In test builds, however, LogKit will abort so that you can fix problems with your logging.

### Extensiblity

Although LogKit comes with a number of ready-built [Endpoint][endpoints] options, developers may desire to create their own. LogKit provides a protocol that any entity may adopt to become a log Endpoint. Conformance is straightforward with just a few properties and one method. LogKit allows you to send your logs wherever you like!


{% include mdlinks.md %}
