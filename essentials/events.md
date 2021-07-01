# Events

You can fire events from within views, components, or by using the global `cbwire` JavaScript object.

### From View

```javascript
<button
    wire:click="$emit('postAdded')">
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

You can register event listeners on a component by defining `this.$listeners` .

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

If any other component on the same page emits a `postAdded` event, the `incrementPostCount` method on the component will be invoked. 

{% hint style="info" %}
When defining your listeners, it a good practice to put your listener names in quotation marks like we have in our component above.   
  
`"postAdded": "incrementPostCount"`

This is because JavaScript keys names are case sensitive, and surrounding your listener names in quotations in CFML will ensure the key name casing is preserved. Without the quotations, the key would be automatically converted to all uppercase `POSTADDED`.
{% endhint %}



## Dynamic Event Listeners

If you need to dynamically name your event listeners, you can do so by overriding the $getListeners\(\) method on your component instead of using `this.$listeners`.

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
<script>
cbwire.on('postAdded', postId => {
    alert('A post was added with the id of: ' + postId);
})
</script>
```

