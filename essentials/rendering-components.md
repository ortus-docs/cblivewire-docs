# Rendering Components

{% hint style="info" %}
You must have a`$renderIt()`method defined on your CFML component. Otherwise, cbwire will throw a`RenderMethodNotFound`exception.
{% endhint %}

{% hint style="info" %}
Be sure that cbwire can bind onto your component's view by including an outer element such as`<div>`. If an outer element is not detected, cbwire will throw a `OuterElementNotFound`exception.
{% endhint %}

```javascript
// File: ./views/wires/myComponent.cfm

<!--- GOOD --->
<cfoutput>
    <div>
        <button wire:click="doSomething">Do Something</button>
    </div>
</cfoutput>

<!--- BAD --->
<cfoutput>
    <button wire:click="doSomething">Do Something</button>
</cfoutput>
```

