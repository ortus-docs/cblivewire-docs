# Loading States

cbwire uses AJAX requests to invoke component actions on our wire objects. There are cases when this may involve a long-running process, such as completing a cart checkout, and the page may not respond instantly to a user event like a click. cbwire allows you to effortlessly display loading states, such as showing/hiding elements, adding/removing classes, or toggling HTML attributes until the server responds.

Loading States can make your apps feel responsive and user-friendly.

## Toggling Elements

Let's take a look at a checkout action that takes way too long.

```javascript
// File: ./wires/Cart.cfc

component extends="cbwire.models.Component"{

    function checkout(){
        sleep( 5000 ); // optimize this code yo!
    }

    function $renderIt(){
        return this.$renderView( "wires/cart" );
    }
}
```

We can add `wire:loading` to our HTML elements to toggle when actions are running.

```javascript
// File: ./views/wires/cart.cfm

<div>
    <button wire:click="checkout">Checkout</button>

    <div wire:loading>
        Processing Payment...
    </div>
</div>
```

After a user clicks the _Checkout_ button, the _Processing Payment_ output will display until the `checkout()` action has been completed, which in this case would be for 5 seconds because we are calling `sleep( 5000 )`.

