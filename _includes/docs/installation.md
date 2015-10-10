{% case include.family %}

{% when 1.0 or 1.1 %}
    {% assign supports =                'iOS 8+, OS X 10.9+' %}
    {% assign supports_legacy =         'iOS 7+, OS X 10.9+' %}
    {% if include.family == 1.0 %}
        {% assign grouping_text =       'the top LogKit for an iOS target, or the bottom LogKit for OS X' %}
        {% assign grouping_image_link = 'img-installation3' %}
    {% else %}
        {% assign grouping_text =       'the top LogKit for an OS X target, or the bottom LogKit for iOS' %}
        {% assign grouping_image_link = 'img-installation3v2' %}
    {% endif %}
    {% assign source_selection = 'the `LogKit.swift` file' %}

> * iOS 7.0 or greater
> * OS X 10.9 or greater
> * Xcode 6.3 or 6.4 with Swift 1.2
>
> Note: For Xcode 7 and Swift 2 compatibility, please check out [LogKit 2][docs-2_0].

{% when 2.0 %}
    {% assign supports =            'OS X 10.9+, iOS 8+, watchOS 2+' %}
    {% assign supports_legacy =     'OS X 10.9+, iOS 7+, watchOS 2+' %}
    {% assign grouping_text =       'the top LogKit for an OS X target, the middle LogKit for iOS, or the bottom for watchOS' %}
    {% assign grouping_image_link = 'img-installation3v3' %}
    {% assign source_selection =    'all of the `.swift` files' %}

> * OS X 10.9 or greater
> * iOS 7.0 or greater
> * watchOS 2.0 or greater
> * Xcode 7 with Swift 2
>
> Note: For Xcode 6 and Swift 1.2 compatibility, please check out [LogKit 1.1][docs-1_1].

{% endcase %}


There are a few ways to install LogKit. You may choose any one method from those below. After completing installation, visit the [usage guide][usage] to get started.

### CocoaPods

> Supports {{ supports }}

[CocoaPods][install-cocoapods] version 0.38 or higher is required. Include LogKit in your Podfile:

{% highlight ruby %}
use_frameworks!
pod 'LogKit', '~> {{ include.family }}'
{% endhighlight %}

For more information on using CocoaPods, read the [guide][cocoapods].

### Carthage

> Supports {{ supports }}

Include LogKit in your Cartfile:

{% highlight text %}
github "logkit/logkit" ~> {{ include.family }}
{% endhighlight %}

For more information on getting started with Carthage, visit the [repo][carthage].

### Embedded Framework

> Supports {{ supports }}

[Download LogKit][gh-release]. Include `LogKit.xcodeproj` within your project (second level, below your project root, as a sub-project). The LogKit project icon should be indented slightly to the right relative to your main project's icon.

![Embedded Installation Image 1][img-installation1]

Select your main project's target, and add LogKit as an Embedded Binary in the General tab.

![Embedded Installation Image 2][img-installation2]

Choose {{ grouping_text }}. You may choose from either grouping.

![Embedded Installation Image 3][{{ grouping_image_link }}]

### Source

> Supports {{ supports_legacy }}
>
> Integrating the LogKit source is the only way to include LogKit in projects targeting iOS 7. When this installation method is used, skip the `import LogKit`.

[Download LogKit][gh-release]. Add {{ source_selection }} found in the `Source` directory to your project. No other steps are necessary for installation.


{% include links.md doc_version=page.family %}
