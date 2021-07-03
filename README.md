---
description: >-
  cbwire is a drop-in module for ColdBox that makes building dynamic and
  reactive interfaces incredibly easy, without leaving the comfort of ColdBox
  and CFML.
---

# Introduction

## cbwire - v1.0

**There's so much to building modern web apps these days.** [ColdBox](https://coldbox.ortusbooks.com/) makes things easy for us on the server-side, but what about our front-end development? ****JavaScript frameworks such as Vue and React are powerful. They have changed the way most of us build web apps, but they've also introduced a great deal of complexity, as well as a significant learning curve when creating our applications.

**What if there was a way to build dynamic web applications that look and feel just like your Vue or React web apps, with little to no JavaScript, and while never leaving CFML?** Impossible, you say? **Nay,** we say!

Introducing **cbwire: Reactivate your CFML!** 

## A real-time search component built with cbwire in minutes...

```javascript
// File: ./wires/SearchUsers.cfc

component
    extends="cbwire.models.Component"
{

    // Wirebox injection ( wee! )
    property
        name="userService"
        inject="UserService@MyModule";

    // Local data property that hold's the search typed into the UI
    this.$data = {
        "search": ""
    };

    // Render our view
    function $renderIt(){
        return this.$renderView(
            "wires/searchUsers",
            { "users" : userService.findBySearch( this.$data.search ) }
        );
    }

}

```

```markup
// File: ./views/wires/searchUsers.cfm

<cfoutput>
<div>
    <input 
        wire:model="search" 
        type="text" 
        placeholder="Search users..."
    />

    <ul>
        <cfloop array="#args.users#" index="user">
            <li>#user.getUsername()#</li>
        </cfloop>
    </ul>
</div>
</cfoutput>
```

Now that you've created your cbwire component and view, you can include this anywhere in your app using our `wire()` helper method.

```markup
// File ./layouts/main.cfm

...
<cfoutput>
<body>
    <!-- 
        Renders our search users form and updates
        in real-time as user types
    -->
    #wire( "SearchUsers" )#
</body>
</cfoutput>
...
```

Let's reflect on what just happened.

1. cbwire renders the initial component out with our `.cfm` page, which means it's SEO- friendly.
2. When a user types into the search, cbwire makes an AJAX request to the server with the updated state.
3. The server re-renders the component and responds with the new HTML.
4. cbwire utilizes the amazing [Livewire](https://laravel-livewire.com/) JavaScript library to mutate the DOM based on our state changes.

More reflecting...

* We built a real-time search in a matter of just a few minutes.
* We didn't use any JavaScript.
* We didn't have to worry about webpack configuration or compilation. 
* We didn't create an API endpoint or worry about any of the complexities that an API introduces.
* We never left CFML.🥰 
* We used awesome baked-in [ColdBox](https://coldbox.org/) features, such as view rendering and dependency injection w/ [WireBox](https://wirebox.ortusbooks.com/).

## Fantastic, right?

We're just getting warmed up! cbwire has transformed the way we are building apps, and we think you're going to love it also. 

Browse through the other sections of this documentation to see just how much cbwire can modernize your applications and improve your development experience. 

## Credits

cbwire wouldn't even exist if it wasn't for the awesome efforts of Caleb Porzio \( creator of [Livewire](https://laravel-livewire.com/), also [Alpine.js](https://github.com/alpinejs/alpine) \) and the PHP Laravel community. Livewire was created for use with the PHP framework Laravel. cbwire is a port of the existing functionality over to CFML and the ColdBox framework.

The cbwire module for ColdBox is written and maintained by Grant Copley, Luis Majano, and [Ortus Solutions](https://www.ortussolutions.com/).

## Project Support

If cbwire makes you happy, please consider becoming one of our lovingly esteemed [Patreon supporters](https://www.patreon.com/ortussolutions).

