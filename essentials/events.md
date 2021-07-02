# Events

You can fire events from within views, components, or by using the global `cbwire` JavaScript object.

### From View

```javascript
<button
    wire:click="$emit( 'postAdded' )">
```

### From Component

```javascript
this.$emit( "postAdded" );
```

### From Javascript Global

```javascript
<script>
    cbwire.emit( 'postAdded' )
</script>
```

## Event Listeners

You can register event listeners on a component by defining `this.$listeners`.

```javascript
component extends="cbwire.models.Component"{

	this.$listeners = {
		"postAdded": "incrementPostCount"
	};

	function incrementPostCount(){
		// This is called when the postAdded event is emitted.
	}

	...
}
```

cbwire will invoke the `incrementPostCount` method on the component if any other component on the same page emits a `postAdded` event. 

{% hint style="info" %}
When defining your listeners, it is good to put your listener's names in quotation marks, as we have in our component above.   
  
`"postAdded": "incrementPostCount"`

JavaScript keys names are case-sensitive. You can preserve the key casing in CFML by surrounding your listener names in quotations. Without the quotations, CFML will convert the key to all uppercase, such as `POSTADDED`.
{% endhint %}

## Dynamic Event Listeners

If you need to name your event listeners dynamically, you can override the `$getListeners()` method on your cbwire component.

```javascript
component extends="cbwire.models.Component"{

    function $getListeners(){
        return {
		 	      "postAdded": "postListener#0 + 1#" // postListener1
		    }
	  }
	...
}
```

## Event Listeners In JavaScript

```javascript
// File: ./views/wires/myView.cfm
<script>
    cbwire.on('postAdded', postId => {
        alert('A post was added with the id of: ' + postId);
    })
</script>
```

