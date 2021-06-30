# Rendering Components

{% hint style="info" %}
You must have a`$renderIt()`method defined on your component, otherwise a  `RenderMethodNotFound`exception will be thrown.
{% endhint %}

{% hint style="info" %}
Be sure that your rendered HTML includes an outer element such as `<div>` that cbLivewire can bind to. If an outer element is not detected, an `OuterElementNotFound` exception is thrown
{% endhint %}

