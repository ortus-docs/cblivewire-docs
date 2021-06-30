# Rendering Components

{% hint style="info" %}
You must have a`$renderIt()`method defined on your CFML component, otherwise a  `RenderMethodNotFound`exception will be thrown.
{% endhint %}

{% hint style="info" %}
Be sure that your rendered HTML includes an outer element such as `<div>` that cbLivewire can bind to. If an outer element is not detected, an `OuterElementNotFound` exception is thrown
{% endhint %}

```javascript
// File: ./views/livewire/myComponent.cfm

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

