---
description: >-
  cbwire is a ColdBox module that makes building reactive, dynamic, and modern
  interfaces delightfully easy without leaving the comfort of CFML.
---

# Introduction

![](.gitbook/assets/cbwire300.png)

## cbwire - v1.0

Building modern CFML apps has become a bit complicated. [ColdBox](https://coldbox.ortusbooks.com/) makes server-side programming a cinch, but what about our front-end development? Front-end frameworks such as Vue and React have transformed our apps and are undoubtedly powerful. Still, they’ve also introduced some complexity and added a significant learning curve when creating web applications.

What if you could create applications that look and feel just like your Vue or React web apps but written primarily with CFML. Impossible, you say? Nay, we say!

Introducing **cbwire: Power-up your CFML!** 

## Let's create a quick reactive counter in cbwire...

Install [CommandBox](https://www.ortussolutions.com/products/commandbox), then from your terminal, run:

```bash
mkdir cbwire-demo
cd cbwire-demo
box create app .
box install cbwire
box server start
```

Let's add Livewire styling and script references to our layout, and also include a new cbwire component we will create called _Counter_.

```markup
<-- ./layouts/Main.cfm -->
<cfoutput>
<!doctype html>
<html lang="en">
<head>
    #wireStyles()#
</head>
<body>
    #wire( "Counter" )#
    #wireScripts()#
</body>
</html>
</cfoutput>

```

Let's create our _Counter_ cbwire component.

```javascript
// File: ./wires/Counter.cfc

component extends="cbwire.models.Component" {

    // Reactive Data Properties
    variables.data = {
        "counter": "0"
    };

    // Action to increment counter
    function increment(){
        variables.data.counter += 1;
    }

    // Tell cbwire where our Counter template is
    function renderIt(){
        return this.renderView(
            "wires/counter"
        );
    }

}

```

```markup
<!-- ./views/wires/counter.cfm -->
<cfoutput>
<div>
    <div>Count: #args.counter#</div>
    <button wire:click="increment">
        +
    </button>
</div>
</cfoutput>
```

Now that you've created your cbwire _Counter_ component and template, you can include this in any layout or view throughout your app using our `wire()` helper method.

Refresh the page, and you find a reactive Counter that increments when you hit the plus button.

![](.gitbook/assets/image.png)

Let's reflect on what just happened.

1. cbwire renders our _Counter_ component with our `.cfm` page. You can View Source to see this. This means cbwire is SEO-friendly.
2. When a user clicks the plus button, cbwire makes an AJAX request to the server and triggers the _increment_ action.
3. cbwire updates the counter state
4. cbwire re-renders the component template and returns the updated HTML in the AJAX response
5. cbwire is using the amazing [Livewire](https://laravel-livewire.com/) JavaScript library to mutate the DOM based on our state changes.

* We built a reactive counter.
* We're not refreshing the page.
* We didn't write any JavaScript.
* We didn't have to worry about webpack configuration or compilation. 
* We never left CFML.🤓 
* We used baked-in [ColdBox](https://coldbox.org/) features, such as view rendering and dependency injection w/ [WireBox](https://wirebox.ortusbooks.com/).

## Fantastic, right?

We're just getting warmed up! cbwire has transformed the way we are building apps, and we think you're going to love it also. 

## Credits

cbwire wouldn't even exist if it wasn't for the impressive efforts of Caleb Porzio \( creator of [Livewire](https://laravel-livewire.com/), also [Alpine.js](https://github.com/alpinejs/alpine) \) and the PHP Laravel community. Caleb created Livewire for use with the PHP framework Laravel. cbwire is a port of the Livewire functionality to ColdBox and CFML, with some additional goodies sprinkled in.

The cbwire module for ColdBox is written and maintained by [Grant Copley](https://twitter.com/grantcopley), [Luis Majano](https://twitter.com/lmajano), and [Ortus Solutions](https://www.ortussolutions.com/).

## Project Support

If cbwire makes you😍, please consider becoming one of our lovingly esteemed [Patreon supporters](https://www.patreon.com/ortussolutions).

