{% case include.family %}

{% else %}


Include LogKit in your Cartfile:

{% highlight text %}
github "logkit/logkit" ~> {{ include.family }}
{% endhighlight %}

For more information on getting started with Carthage, visit the [repo][carthage].


{% endcase %}
