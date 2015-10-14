{% case include.family %}

{% else %}


A keen observer of the method signatures for each of the above logging methods may note that there are additional parameters included in each method (as seen in Xcode or [CocoaDocs][cocoadocs]). These parameters are `functionName`, `filePath`, `lineNumber`, and `columnNumber`. They are not mentioned above because they are meant to be ignored.

Each of these parameters will default to [special Swift variables][swift-specials] that automatically capture the function name, file name, line number, and column number of the code from which each of your Log Entries was created. Application developers should omit these parameters from their logging calls, allowing LogKit to correctly capture the scope of each call and save it in the [Log Entry][entries].


{% endcase %}
