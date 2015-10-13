{% case include.family %}

{% when 1.0 or 1.1 %}


> * iOS 7.0 or greater
> * OS X 10.9 or greater
> * Xcode 6.3 or 6.4 with Swift 1.2
>
> Note: For Xcode 7 and Swift 2 compatibility, please check out [LogKit 2][docs-2_0].


{% else %}


> * OS X 10.9 or greater
> * iOS 7.0 or greater
> * watchOS 2.0 or greater
> * Xcode 7 with Swift 2
>
> Note: For Xcode 6 and Swift 1.2 compatibility, please check out [LogKit 1.1][docs-1_1].


{% endcase %}
