# Data Properties

Similar to VueJS and other frontend JavaScript frameworks, you can define and initialize reactive properties on your cbwire components using `variables.$data`. When data properties are mutated, the UI will update also.

```javascript
// File: wires/BestMovies.cfc

component extends="cbwire.models.Component"{
    variables.$data = {
        "topMovies": [
            "Back To The Future",
            "Karate Kid",
            "Ferris Bueller's Day Off"
        ]
    };
    ...
}
```

## Referencing Properties

You can reference a property directly in your component using `variables.$data.[ property name ]`.

```javascript
// File: wires/BestMovies.cfc

component extends="cbwire.models.Component"{

    // Data properties
    variables.$data = {
        "topMovies": [
            "Back To The Future",
            "Karate Kid",
            "Ferris Bueller's Day Off"
        ]
    };
    
    // Action called from UI
    function addAMovie(){
        variables.$data.topMovies.append( "Ghostbusters" );
    }
    ...
}
```

You can also reference any defined properties from your cbwire component view using `args.[ property name  ]`.

```javascript
// File: views/wires/bestMovies.cfm

<cfoutput>
<div>
    <h1>Top Movies</h1>
    <ul>
        <cfloop array="#args.topMovies#" index="movie">
            <li>#movie</li>
        </cfloop>
    </ul>
</div>
</cfoutput>
```

## Security

Your component's private variables scope will store your data property definitions and current values, but it's necessary to be cautious about what you store. cbwire communicates with the server via background AJAX requests and includes the current state of the data properties within those requests.

{% hint style="warning" %}
You should never store sensitive data \( such as passwords \) that you wouldn't want your application's users to see.
{% endhint %}

{% hint style="info" %}
cbwire includes the current state of the data properties during requests in order to determine what has changed and if cbwire should update the [DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction).
{% endhint %}



