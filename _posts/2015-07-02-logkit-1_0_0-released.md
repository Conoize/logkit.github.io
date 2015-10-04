---
layout: post
title: LogKit 1.0.0 Released
tags: releases
author: Justin Pawela
---

LogKit is a new iOS and OS X logging framework built for Swift applications. It was built for simplicity, efficiency, safety, and extensibility.

There are other logging libraries already available for Swift apps. LogKit was created because each of the others seemed either simple but inflexible or convoluted and over-built. We wanted a framework we could use with minimal setup early in the app development process, then tweak later when it made sense in the context of our app. No one logs just to log, but when we do log we need it to work on our own terms.

 With LogKit, we strive to strike a balance between simplicity and extensibility. Hopefully, this goal manifests itself right away  via the simple [set up process][usage]. One import, one [Logger][loggers], and you're logging. We include built-in destinations ([Endpoints][endpoints]) for various needs - including several varieties of console, file, and HTTP service - that are fully configurable. We even allow you to build your own Endpoints by conforming to a simple protocol. But with everything we include, we try to make setup dead-simple by using sensible defaults whenever possible.

Beyond simplicity and extensibility, LogKit strives to differentiate itself with its efficiency and safety. We wanted to take advantage of both new and established technologies that Apple's environment affords. Concurrency is used in LogKit, but only where it makes sense, and we try to let the system do the heavy lifting (file I/O, networking, etc.). Using Swift, everything is built to break gracefully in a shipping app. Optionals are used throughout, and a failed data conversion or entry output will simply be skipped.

There is room to grow. This is a first release. Swift 2 is coming in a few months. We hope that LogKit will evolve with both Swift and its community's needs.

For more about the project, see LogKit's [about page][about], or check out the [documentation][docs] to get started.


 {% include links.md doc_version=1.0 %}
