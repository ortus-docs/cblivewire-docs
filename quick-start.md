# Quick Start

## Installing cbLivewire

With [CommandBox](https://commandbox.ortusbooks.com/) installed, you can install cbLivewire by running the following command from your project's root folder.

`box install cbLivewire`

## Add To Your Layout

In order for Livewire to do its magic, you will need to place the `livewireStyles()`  and `livewireScripts()` helper methods in your layout view file. 

```text
// File: ./layouts/main.cfm

<cfoutput>
<!doctype html>
<html>
<head>
	#livewireStyles()#
</head>
<body>
	<h1>cbLivewire Is Awesome</h1>
	<div>
		#renderView()#
	</div>

	#livewireScripts()#
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



