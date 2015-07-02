---
layout: docpage
title: Installation
---

> * iOS 7.0 or greater
> * OS X 10.9 or greater
> * Xcode 6.3 or greater
>
> LogKit currently requires Swift 1.2. A Swift 2 version is in the works.

There are a few ways to install LogKit. You may choose any one method from those below. After completing installation, visit the [usage guide][usage] to get started.

### CocoaPods

> Supports iOS 8+, OS X 10.9+

[CocoaPods][install-cocoapods] version 0.36 or higher is required. Include LogKit in your Podfile:

{% highlight ruby %}
use_frameworks!
pod 'LogKit', '~> 1.0'
{% endhighlight %}

For more information on using CocoaPods, read the [guide][cocoapods].

### Carthage

> Supports iOS 8+, OS X 10.9+

Include LogKit in your Cartfile:

{% highlight text %}
github "logkit/logkit" >= 1.0
{% endhighlight %}

For more information on getting started with Carthage, visit the [repo][carthage].

### Embedded Framework

> Supports iOS 8+, OS X 10.9+

Include `LogKit.xcodeproj` within your project (second level, below your project root, as a sub-project). The LogKit project icon should be indented slightly to the right relative to your main project's icon.

![Embedded Installation Image 1][img-embedded1]

Select your main project's target, and add LogKit as an Embedded Binary in the General tab.

![Embedded Installation Image 2][img-embedded2]

Choose the top LogKit for an iOS target, or the bottom LogKit for OS X. You may choose from either grouping.

![Embedded Installation Image 3][img-embedded3]

### Source

> Supports iOS 7+, OS X 10.9+
>
> Integrating the LogKit source file is the only way to include LogKit in projects targeting iOS 7. When this installation method is used, skip the `import LogKit`.

Add `LogKit.swift` (found in the `Sources` directory) to your project. No other steps are necessary for installation.


{% include mdlinks.md %}
