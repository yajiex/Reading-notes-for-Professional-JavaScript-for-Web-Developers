# Chapter 11: DOM Extensions

* `querySelectorAll` returns a static instance of `NodeList`, its underlying implementation acts as a snapshot of elements rather than a dynamic query that is constantly reexecuted against a document.
* If multiple class names are specified for `getElementsByClassName()`, the order is considered unimportant.
* HTML5 introduces a way to manipulate class names: `classList`, `add(value)`, `contains(value)`, `remove(value)`, `toggle(value)`
* `document.activeElement` always contains a pointer to the DOM element that currently has focus. By default, `document.activeElement` is set to `document.body` when the document is first loaded. Before the document is fully loaded, `document.activeElement` is null.
