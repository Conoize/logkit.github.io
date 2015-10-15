---
layout: post
title: LogKit 2.0.2 and 1.1.1 Released
tags: releases
author: Justin Pawela
---

Both LogKit 2.0.2 and 1.1.1 fix the ordering of products in Xcode to match the installation documentation. This issue would not affect existing LogKit users, but may have made it difficult for new users to set up LogKit in a new project.

Also contained are a few minor documentation updates.

[The 2.0.2 release notes can be found here.][gh-release]

[The 1.1.1 release notes can be found here.]({{ site.releases | where:'family',1.1 | map:'download_link' }})


{% include links.md doc_version=2.0 %}
