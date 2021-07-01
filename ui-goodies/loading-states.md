# Loading States

_cbwire_ will perform a server request every time an action is invoked. There are cases when this may involve a long-running process, such as completing a cart checkout, and the page may not react immediately to a user event like a click. _cbwire_ allows you to easily display loading states, such as showing/hiding elements, adding/removing classes, or toggling HTML attributes until the server responds.

This can make your apps feel more much more responsive and user-friendly.

## Quick Example

```text
component extends="cbwire.models.Component"{

    function checkout(){
        sleep( 5000 );
    }

    function $renderIt(){
        return this.$renderView( "myView" );
    }
}
```

```text
// File: ./views/wires/myView.cfm

<div>
    <button wire:click="checkout">Checkout</button>

    <div wire:loading>
        Processing Payment...
    </div>
</div>
```

After a user clicks the _Checkout_ button, the _Processing Payment..._ output will display until the `checkout()` action has been completed, which in this case would be for 5 seconds because we are calling `sleep( 5000 )`.

{% hint style="info" %}
_cbwire_ uses _Livewire's_ 2.x JavaScript library for all front-end functionality. You can refer to the [Loading States](https://laravel-livewire.com/docs/2.x/loading-states) page from the _Livewire_ documentation for detailed information on Loading States and how to use them.
{% endhint %}

