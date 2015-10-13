{% case include.family %}

{% when 1.0 or 1.1 %}


> Integrating the LogKit source is the only way to include LogKit in projects targeting iOS 7. When this installation method is used, skip the `import LogKit`.

[Download LogKit][gh-release]. Add the `LogKit.swift` file found in the `Source` directory to your project. No other steps are necessary for installation.


{% else %}


> Integrating the LogKit source is the only way to include LogKit in projects targeting iOS 7. When this installation method is used, skip the `import LogKit`.

[Download LogKit][gh-release]. Add all of the `.swift` files found in the `Source` directory to your project. No other steps are necessary for installation.


{% endcase %}
