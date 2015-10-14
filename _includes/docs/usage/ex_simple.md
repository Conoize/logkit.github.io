{% case include.family %}

{% else %}


> AppDelegate.swift

{% highlight swift linenos %}
import UIKit
import LogKit

let log = LXLogger()

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate, UISplitViewControllerDelegate {
    // ...

    func application(application: UIApplication, didFinishLaunchingWithOptions launchOptions: [NSObject : AnyObject]?) -> Bool {

        log.debug("Hello Internet!")

        return true
    }
}
{% endhighlight %}

This simple example initializes a [Logger][loggers] with a standard [Console Endpoint][ep-console]. Lines 2, 4, and 12 contain the relevant code for getting LogKit set up quickly and making your first [Log Entry][entries].

Because the Logger instance `log` is created as a global, you may now make logging calls from any of your project's source files.


{% endcase %}
