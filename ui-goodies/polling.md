# Polling

You can add a `wire:poll` annotation to your elements to poll for changes for a set interval. By default, this interval is set to every _2 seconds_.

```markup
<div wire:poll>
    Current time: #now()#
</div>
```

You can append a different interval time to your annotation as well.

```markup
<div wire:poll.5000ms>
    Current time: #now()#
</div>
```

{% hint style="info" %}
Polling for changes over AJAX is lightweight and is a good alternative to other strategies such as Pusher or WebSockets. 
{% endhint %}

### Invoking Method

If you would like to invoke a method during each poll interval, you can do so by specifying a method name.

```markup
<div wire:poll="checkIfCoffeeIsReady">
    Current time: #now()#
</div>
```



