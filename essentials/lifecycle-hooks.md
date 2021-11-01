# Lifecycle Events

## Initial Component Rendering

![](<../.gitbook/assets/image (2).png>)

## mount( parameters, event, rc, prc )

Runs once immediately after a component is instantiated before `renderIt()` is called.

```javascript
component extends="cbwire.models.Component" {

    function mount( parameters, event, rc, prc ){
        variables.data.incomingValue = event.getValue( "someField" );
    }

}
```

## &#x20;
