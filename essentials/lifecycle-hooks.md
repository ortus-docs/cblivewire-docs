# Lifecycle Hooks

###  this.preEmit\( string eventName, struct parameters \)

### this.postEmit\( string eventName, struct parameters \)

Executes before and after **the current** cbwire component emits **any** event.

```javascript
// File: ./wires/MovieList.cfc

component extends="cbwire.models.Component"{

    /**
    * Fire an event when the user clicks a button.
    */
    function clickButton(){
        this.emit( "IndianaJones", [ "And","The","Last","Crusade" );
    }

    function preEmit( string eventName, struct parameters ){
        // Fires before we emit "IndianaJones"         
    }
    
    function postEmit( string eventName, struct parameters ){
        // Fires after we emit "IndianaJones"         
    }

    function renderIt(){
        return this.renderView( "wires/movieList" );
    }
    

}
```

{% hint style="info" %}
The `preEmit` and `postEmit` lifecycle hooks are executed when events are emitted **within the same component**, not when events are emitted from other components.
{% endhint %}

You can also target specific emits by appending the event to your function name, such as `preEmitIndianaJones` and `postEmitIndianaJones`.

```javascript
// File: ./wires/MovieList.cfc

component extends="cbwire.models.Component"{
    ...
    function preEmitIndianaJones( struct parameters ){}
    
    function postEmitIndianaJones( struct parameters ){}
    ...
}
```

##  

### preHyrdrate\( wireRequest \) 

### postHydrate \( wireRequest \)

### preGetter\( dataProperty \)

### postGetter\( dataProperty \)

### preSetter\( dataProperty, value \)

### postSetter\( dataProperty, value \)

### preRenderView\( view, args \)

### postRenderView\( view, args \)

### preListener\( listener \)

### postListener\( listener \)

### preAction

### postAction

### preComputed

### postComputed

