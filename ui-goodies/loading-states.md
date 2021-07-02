# Loading States

cbwire uses AJAX requests to invoke component actions on our wire objects. There are cases when this may involve a long-running process, such as completing a cart checkout, and the page may not respond instantly to a user event like a click. cbwire allows you to effortlessly display loading states, such as showing/hiding elements, adding/removing classes, or toggling HTML attributes until the server responds.

Loading States can make your apps feel responsive and user-friendly.

## Toggling Elements

Let's take a look at a checkout action that takes too long.

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

We can add `wire:loading` on our HTML elements to display content when actions are running.

```javascript
// File: ./views/wires/cart.cfm

<div>
    <button wire:click="checkout">Checkout</button>

    <div wire:loading>
        Processing Payment...
    </div>
</div>
```

After a user clicks the _Checkout_ button, the _Processing Payment_ output will display until the `checkout()`action has been completed. Once the action completes, the output will disappear.

## Delay Toggling

Sometimes your component actions run so quickly that the user will not have time to see the elements you want to display. Even worse, they may see a flicker on the page and wonder what happened. You can add a `.delay` modifier to delay displaying your HTML elements for _200ms_.

```javascript
<div wire:loading.delay>...</div>
```

##  Display Property

Loading elements are set with a CSS property of `display: inline-block;` by default. You can override this behavior by using various modifiers.

```javascript
<div wire:loading.flex>...</div>
<div wire:loading.grid>...</div>
<div wire:loading.inline>...</div>
<div wire:loading.table>...</div>
```

