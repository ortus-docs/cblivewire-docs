---
description: >-
  cbLivewire is a drop-in module for ColdBox that makes building
  dynamic/reactive interfaces incredibly easy, without leaving the comfort of
  ColdBox and CFML.
---

# Introduction

## cbLivewire - v1.0

**There's so much to building modern web apps these days.** [ColdBox](https://coldbox.ortusbooks.com/) makes things easy for us on the server-side, but what about our front-end development? ****JavaScript frameworks such as Vue and React are incredibly powerful and have changed the way most of us build web apps, but they've also introduced a great deal of complexity, as well as a significant learning curve when creating our applications.

**What if there was a way to build dynamic web applications that look and feel just like your Vue or React web apps, with little to no JavaScript, and while never leaving CFML?**

Impossible you say? **Nay** we say! Introducing **cbLivewire : Reactivate your CFML!**

## A real-time search component built with cbLivewire in minutes...

```javascript
// File: ./livewire/SearchUsers.cfc

component extends="cbLivewire.models.Component" accessors="true" {

    // Wirebox injection ( wee! )
    property name="userService" inject="UserService@MyModule";

    // Local property that hold's the search typed into the UI
    property name="search" default="";
    
    // Render our view
    function $renderIt(){
        return this.$renderView( "cbLivewire/searchUsers", {
            users: userService.findBySearch( this.getSearch() )
        } );
    }

}

```

```markup
// File: ./views/livewire/searchUsers.cfm

<cfoutput>
<div>
    <input wire:model="search" type="text" placeholder="Search users..."/>

    <ul>
        <cfloop array="#args.users#" index="user">
            <li>#user.getUsername()#</li>
        </cfloop>
    </ul>
</div>
</cfoutput>
```

Now that you've defined your cbLivewire component and view, you can include this anywhere in your app using cbLivewire's `livewire()` helper method.

```markup
// File ./layouts/main.cfm

...
<cfoutput>
<body>
    <!-- Renders our search users form and updates in real-time as user types -->
    #livewire( "SearchUsers" )#
</body>
</cfoutput>
...
```

Let's take a moment to reflect on what in the world just happened.

* Livewire renders the initial component out with our .cfm page, which means it's SEO friendly.
* When a user types into the search, Livewire makes an AJAX request to the server with the updated state.
* The server re-renders the component and responds with the new HTML.
* Livewire intelligently mutates the DOM based on our state changes.

More reflecting...

* We built a real-time search in a matter of just a few minutes.
* We didn't use any JavaScript.
* We didn't have to worry about webpack configuration or compilation. 
* We didn't create an API endpoint or worry about any of the complexities that an API introduces.
* We never left CFML.
* We used awesome baked-in ColdBox features, such as view rendering and dependency injection w/ [WireBox](https://wirebox.ortusbooks.com/).

## Unreal, right?

We're just getting warmed up! Browse through the other sections of this documentation to see just how much **cbLivewire** can transform your applications and improve your development experience. This has changed the way we are building apps, and we think you're going to love it also.

## Credits

cbLivewire wouldn't even exist if it wasn't for the awesome efforts of Caleb Porzio \( creator of Livewire, also Alpine.js \) and the PHP Laravel community. Livewire was originally created for use with the PHP framework Laravel. **cbLivewire** is a port of the existing functionality over to ColdBox and CFML.

The **cbLivewire** module for ColdBox is written and maintained by Grant Copley, Luis Majano, and [Ortus Solutions](https://www.ortussolutions.com/).

