# Lifecycle Events

## Component Wiring

![](<../.gitbook/assets/image (3).png>)

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
