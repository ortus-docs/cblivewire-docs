---
description: >-
  cbwire is a ColdBox module that makes building reactive, dynamic, and modern
  interfaces delightfully easy without leaving the comfort of CFML.
---

# Introduction

![](.gitbook/assets/logo%20%281%29.png)

## cbwire - v1.0

Building modern CFML apps has become a bit complicated. [ColdBox](https://coldbox.ortusbooks.com/) makes server-side programming a cinch, but what about our front-end development? Front-end frameworks such as Vue and React have transformed our apps and are undoubtedly powerful. Still, they’ve also introduced some complexity and added a significant learning curve when creating web applications.

What if you could create applications that look and feel just like your Vue or React web apps but written primarily with CFML. Impossible, you say? Nay, we say!

Introducing **cbwire: Reactivate your CFML!** 

## A real-time movie search component built with cbwire in minutes...

```javascript
// File: ./wires/SearchMovies.cfc

component extends="cbwire.models.Component" {

    // Wirebox injection ( wee! )
    property
        name="movieService"
        inject="MovieService@MyModule";

    // Our local data properties
    variables.$data = {
        // Hold's the search typed into the UI
        "search": ""
    };

    // Render our view
    function $renderIt(){
        return this.$renderView(
            "wires/searchMovies",
            { "movies" : movieService.findBySearch( variables.$data.search ) }
        );
    }

}

```

```markup
// File: ./views/wires/searchMovies.cfm

<cfoutput>
<div>
    <input 
        wire:model="search" 
        type="text" 
        placeholder="Search movies..."
    />

    <ul>
        <cfloop array="#args.movies#" index="movie">
            <li>#movie.getName()#</li>
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
        Renders our movie search form and updates
        in real-time as user types
    -->
    #wire( "SearchMovies" )#
</body>
</cfoutput>
...
```

Let's reflect on what just happened.

1. cbwire renders the initial component out with our `.cfm` page, which means it's SEO- friendly.
2. When a user types into the search, cbwire makes an AJAX request to the server with the updated state.
3. The server re-renders the component and responds with the new HTML.
4. cbwire utilizes the excellent [Livewire](https://laravel-livewire.com/) JavaScript library to mutate the DOM based on our state changes.

* We built a real-time search in a matter of just a few minutes.
* We didn't use any JavaScript.
* We didn't have to worry about webpack configuration or compilation. 
* We didn't create an API endpoint or worry about any of the complexities that an API introduces.
* We never left CFML.🥰 
* We used baked-in [ColdBox](https://coldbox.org/) features, such as view rendering and dependency injection w/ [WireBox](https://wirebox.ortusbooks.com/).

## Fantastic, right?

We're just getting warmed up! cbwire has transformed the way we are building apps, and we think you're going to love it also. 

Browse through the other sections of this documentation to see just how much cbwire can modernize your applications and improve your development experience. 

## Credits

cbwire wouldn't even exist if it wasn't for the impressive efforts of Caleb Porzio \( creator of [Livewire](https://laravel-livewire.com/), also [Alpine.js](https://github.com/alpinejs/alpine) \) and the PHP Laravel community. Caleb created Livewire for use with the PHP framework Laravel. cbwire is a port of the Livewire functionality to ColdBox and CFML, with some additional goodies sprinkled in.

The cbwire module for ColdBox is written and maintained by Grant Copley, Luis Majano, and [Ortus Solutions](https://www.ortussolutions.com/).

## Project Support

If cbwire makes you happy, please consider becoming one of our lovingly esteemed [Patreon supporters](https://www.patreon.com/ortussolutions).

