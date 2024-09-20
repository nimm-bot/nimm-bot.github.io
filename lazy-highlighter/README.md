# LazyHighlighter initialization and options

Lazy highlighter is a simple vanilla JS library for pointing out HTML elements on mouse events.

## Initialization

To start using Lazy Highlighter library, include files from src folder in Your HTML code:

```
<script src="{directory_path}/lazy-highlighter.js" type="text/javascript"></script>
<link href="{directory_path}/lazy-highlighter.css" rel="stylesheet">
```
... or use CDN from GitHub repository:
```
<script src="https://nimm-bot.github.io/lazy-highlighter/src/js/lazy-highlighter.js" type="text/javascript"></script>
<link href="https://nimm-bot.github.io/lazy-highlighter/src/css/lazy-highlighter.css" rel="stylesheet">
```


Once necessary files are included, append script with this snippet:

```
window.addEventListener('load', function () {
    document.querySelectorAll('[data-lazy-highlighter-activator]').forEach(function (elem) {
        new LazyHighlighter(elem, {});
    });
});
```

The **first argument** of constructor is element that, when hovered on, highlights related elements.

The **second argument** is a JSON object used for setting highlight options.


## Options

Upon calling the constructor, the following options can be assigned in **options** argument:

* **template** (string) - HTML string to use as wrapper. Must contain {highlighted} substring as a placeholder to highlighted element. <br/>
    Defaults to <br/>
    `<div class="lazy-highlighter-container"><div data-lazy-highlighter-background></div>{highlighted}</div></code>`.
* **preset** (string) - Sets highlight style to one of default presets: `DEFAULT`, `BORDER`, `MARKER`.
* **events** (JSON object) - sets callbacks for the following events: `click`, `mouseover`, `mouseleave`. <br/>
    Object keys must match event names and values - callbacks for specific events.

## Methods

Calling the constructor assigns LazyHighlighter property to activator element. The following methods can be called for this property:

* **refresh ()** - Reloads list of affected elements and rebinds events.
* **destroy ()** - Removes LazyHighlighter instance from activator element.
* **highlight (isOn)** - Shortcut function to highlight all elements affected by activator. <br/>
    _isOn_ (null | bool) - if `null`, toggles highlight on/off based on current state. If bool value is used, `true` turns highlight on, `false` - off.
* **setEvent (key, callback)** - Assigns event callback to event name, but doesn't bind it. Please call refresh() to update existing events. <br/>
    _key_ (string) - event to bind a new callback to. Available values: `'click'`, `'mouseover'`, `'mouseleave'` <br/> 
    _callback_ (function) - callback function.
* **setOption (key, value)** - set `options` property, except events. For setting events please see **setEvent()**.

<br/>

Usage examples can be found in demo.html file.
