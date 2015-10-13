{% case include.family %}

{% when 1.0 or 1.1 %}


[CocoaPods][install-cocoapods] version 0.36 or higher is required. Include LogKit in your Podfile:

{% highlight ruby %}
use_frameworks!
pod 'LogKit', '~> {{ include.family }}'
{% endhighlight %}

For more information on using CocoaPods, read the [guide][cocoapods].


{% else %}


[CocoaPods][install-cocoapods] version 0.38 or higher is required. Include LogKit in your Podfile:

{% highlight ruby %}
use_frameworks!
pod 'LogKit', '~> {{ include.family }}'
{% endhighlight %}

For more information on using CocoaPods, read the [guide][cocoapods].


{% endcase %}
