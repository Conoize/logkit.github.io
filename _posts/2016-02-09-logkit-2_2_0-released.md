---
layout: post
title: LogKit 2.2.0 Released
tags: releases
author: Justin Pawela
---

LogKit 2.2.0 includes a few minor feature additions to the family of File Endpoints.

A new API has been exposed for accessing a File Endpoint's `directoryURL` and `currentURL` properties. The `directoryURL` is the URL of the directory in which the Endpoint's log files are stored. The `currentURL` is the URL of the specific file to which the Endpoint is currently writing. These properties are available in all File Endpoints, including `LXFileEndpoint`, `LXRotatingFileEndpoint`, and `LXDatedFileEndpoint`.

Additionally, new notifications have been added to File Endpoints that change files. Before and after changing log files, the Endpoint will post a notification to the default notification center. Notifications will include URLs to the previous, current, and next log file, as appropriate. Both `LXRotatingFileEndpoint` and `LXDatedFileEndpoint` will emit these notifications.

All changes made in this release are backward-compatible and require no action for developers not using the new features.


[The release notes can be found here.][gh-release-2_2_0]


{% include links.md doc_version=2.2 %}
