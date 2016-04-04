---
layout: post
title: LogKit 2.3.0 Released
tags: releases
author: Justin Pawela
---

LogKit 2.3.0 includes an important Advertising ID fix, some new Rotating File Endpoint APIs, and support for Swift 2.2.

#### Advertising ID is now disabled by default

Each [Log Entry][entries] instance contains an Advertising ID property `deviceAdvertisingID`. This property, available in iOS and tvOS, triggers an Apple [IDFA review][IDFA] when submitting applications to the App Store. Because many developers may not need the Advertising ID, and would not wish to be subject to additional reviews and agreements, the ID has been disabled by default. [Enabling the Advertising ID][advertising-id] is simple for those developers who need it.

#### Rotating File Endpoint now allows manual rotation

The [`LXRotatingFileEndpoint`][ep-rotating-file] class has been updated to support manual control of log file rotation. Its initializer now accepts `nil` as the maximum file size, indicating the the Endpoint instance should not rotate automatically. Instead, a developer can call the `rotate()` method of the Endpoint instance to manually trigger a file rotation.

#### Swift 2.2

LogKit has been updated to use Swift 2.2, eliminating a number of compiler warnings caused by deprecations. Xcode 7.3 is required.


[The release notes can be found here.][gh-release-2_3_0]


{% include links.md doc_version=2.3 %}
