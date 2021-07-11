---
description: >-
  You can emit events from your cbwire components, views, and also direct from
  JavaScript. Listeners can be defined to execute specific actions.
---

# Events

You can fire events from within views, components, or by using the global `cbwire` JavaScript object.

### From View

```javascript
<button
    wire:click="$emit( 'movieAdded' )">
```

### From Component

```javascript
this.emit( "movieAdded" );
```

### From Javascript Global

```javascript
<script>
    cbwire.emit( 'movieAdded' )
</script>
```

## Event Listeners

You can register event listeners on a component by defining `variables.listeners`.

```javascript
component extends="cbwire.models.Component"{

	variables.listeners = {
		"movieAdded": "tellEveryone"
	};

	function tellEveryone(){
		// This is called when the movieAdded event is emitted.
	}

	...
}
```

{% hint style="success" %}
cbwire will invoke the `tellEveryone` method on the component if any other component on the same page emits a `movieAdded` event. 
{% endhint %}

{% hint style="info" %}
When defining your listeners, it is good to put your listener's names in quotation marks, as we have in our component above.   
  
`"movieAdded": "tellEveryone"`

JavaScript keys are case-sensitive. You can preserve the key casing in CFML by surrounding your listener names in quotations. Without the quotations, CFML will convert the key to all uppercase, such as `POSTADDED`. 🙃 
{% endhint %}

## Dynamic Event Listeners

If you need to name your event listeners dynamically, you can override the `getListeners()` method on your cbwire component.

```javascript
component extends="cbwire.models.Component"{

    function getListeners(){
        return {
		 	      "movieAdded": "tellEvery#0 + 1#" // tellEvery1
		    }
	  }
	...
}
```

## Event Listeners In JavaScript

```javascript
// File: ./views/wires/myView.cfm
<script>
    cbwire.on( 'movieAdded', movieId => {
        alert( 'A movie was added with the id of: ' + movieId );
    })
</script>
```

