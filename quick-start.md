# Quick Start

## Installing cbwire

With [CommandBox](https://commandbox.ortusbooks.com/) installed, you can install cbwire by running the following command from your project's root folder.

`box install cbwire`

## Add To Your Layout

For cbwire to do its magic, you will need to place the `wireStyles()`  and `wireScripts()` helper methods in your layout view file. 

{% hint style="warning" %}
If you forget to add `wireStyles()` and `wireScripts()` to your layout, cbwire will not work, and your whole day will probably be ruined.
{% endhint %}

```javascript
// File: ./layouts/main.cfm

<cfoutput>
<!doctype html>
<html>
<head>
    #wireStyles()#
</head>
<body>
    <h1>cbwire is fire!</h1>
    <div>
        #renderView()#
    </div>

    #wireScripts()#
</body>
</html>
</cfoutput>
```

## Create Your Component

TODO

## Place Your Component In A View

TODO

## View In Browser

TODO

## Let's Create A Counter Component

TODO

##  



