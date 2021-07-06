# Lifecycle Hooks

###  this.$preEmit\( string eventName, array parameters \)

### this.$postEmit\( string eventName, array parameters \)

Executes before and after **the current** cbwire component emits **any** event. The parameters are provided as an array instead of a named struct because the underlining JavaScript engine requires the order to be preserved for emitted events.

```javascript
// File: ./wires/MovieList.cfc

component extends="cbwire.models.Component"{

    /**
    * Fire an event when the user clicks a button.
    */
    function clickButton(){
        this.$emit( "IndianaJones", [ "And","The","Last","Crusade" );
    }

    function $preEmit( eventName, parameters ){
        // Fires before we emit "IndianaJones"         
    }
    
    function $postEmit( eventName, parameters ){
        // Fires after we emit "IndianaJones"         
    }

    function $renderIt(){
        return this.$renderView( "wires/movieList" );
    }
    

}
```

{% hint style="info" %}
The `$preEmit` and `$postEmit` lifecycle hooks are executed when events are emitted within the same component, not when events are emitted from other components.
{% endhint %}

##  

### $preHyrdrate\( wireRequest \) 

### $postHydrate \( wireRequest \)

### $preGetter\( dataProperty \)

### $postGetter\( dataProperty \)

### $preSetter\( dataProperty, value \)

### $postSetter\( dataProperty, value \)

### $preRenderView\( view, args \)

### $postRenderView\( view, args \)

### $preListener\( listener \)

### $postListener\( listener \)

### $preEmit\( event, args \)

### $preEmitEventname\( args \)

### $postEmit\( event, args \)

### $postEmitEventname\( args \)

### $preAction

### $postAction

### $preComputed

### $postComputed

