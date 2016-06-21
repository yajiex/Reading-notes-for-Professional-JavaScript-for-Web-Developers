# Chapter 11: DOM Extensions

* `querySelectorAll` returns a static instance of `NodeList`, its underlying implementation acts as a snapshot of elements rather than a dynamic query that is constantly reexecuted against a document.
* If multiple class names are specified for `getElementsByClassName()`, the order is considered unimportant.
* HTML5 introduces a way to manipulate class names: `classList`, `add(value)`, `contains(value)`, `remove(value)`, `toggle(value)`
* `document.activeElement` always contains a pointer to the DOM element that currently has focus. By default, `document.activeElement` is set to `document.body` when the document is first loaded. Before the document is fully loaded, `document.activeElement` is null. And `document.hasFocus()` returns a Boolean value indicating if the document has focus.
* The `readyState` property for `document` has two possible values:
  1. `loading` => The document is loading
  2. `complete` => The document is completely loaded
* When in standards mode, `document.compatMode` is equal to `CSS1Compat`; when in quirks mode, `document.compatMode` is `BackCompat`
* The `charset` property indicates the actual character set being used by the document and by default this value is `"UTF-16"`. The `defaultCharset` property indicates what the default character set for the document should be based on default browser and system settings.
