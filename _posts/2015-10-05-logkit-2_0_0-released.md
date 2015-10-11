---
layout: post
title: LogKit 2.0.0 Released
tags: releases
author: Justin Pawela
---

Today marks the release of LogKit 2, a complete overhaul of the LogKit framework. LogKit 2 aims to make LogKit even more useful with the inclusion of new and enhanced Endpoints, watch OS compatibility, and more detailed logging information. Many internal improvements have been made as well, allowing for easier customization and more enhancements in the future.

Upgrading to LogKit 2 is easy, although it will require some minor changes in your code. Many classes have been renamed (a full list is available in the [release notes][gh-release]), and some Endpoint initializers have been updated to reflect new options. Date and Entry formatters have grown into full classes, which allow for more built-in options, more modular customization, and easier initialization. A [migration guide][migration] is available for developers upgrading from LogKit 1 to LogKit 2.

Finally, although development has moved to Swift 2, there may still be some developers using Xcode 6 with Swift 1.2. LogKit 1.1.0 is now available, and it is mostly a forward-compatibility release. Several (but not all) of the name changes that LogKit 2 brings have been brought to 1.1.0, with the intention of allowing developers to upgrade more gradually. LogKit 1.0.x users can upgrade to 1.1.0 without fear, as all changes have been made with backward-compatibility in mind; existing code will continue to work as it does currently. Please read the [LogKit 1.1.0 release announcement][local-1_1_0-announcement] for more information.


[The release notes can be found here.][gh-release]


[local-1_1_0-announcement]: /2015/10/04/logkit-1_1_0-released/
{% include links.md doc_version=2.0 %}
