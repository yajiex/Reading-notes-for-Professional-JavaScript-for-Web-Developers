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
* When a custom data attribute is defined, it can be accessed via the `dataset` property of the element.
* `innerHTML` returns the HTML representing all of the child nodes, including elements, comments, and text nodes.
* `outerHTML` returns the HTML of the element on which it is called, as well as its child nodes.
* `insertAdjacentHTML()` accepts two arguments: the position in which to insert and the HTML text to insert, the first argument must be one of the following values:
  1. `"beforebegin"` => Insert just before the element as a previous sibling
  2. `"afterbegin"` => Insert just inside of the element as a new child or series of children before the first child
  3. `"beforeend"` => Insert just inside of the element as a new child or series of children after the last child
  4. `"afterend"` => Insert just after the element as a next sibling
* Inserting a large amount of new HTML is more efficient through `innerHTML` than through multiple DOM operations to create nodes and assign relationships between them. This is because an HTML parser is created whenever a value is set to `innerHTML` (or `outerHTML`). This parser runs in browser-level code (often written in C++), which is must faster than JavaScript.
* The `scrollIntoView()` method exists on all HTML elements and scrolls the browser window or container element so the element is visible in the viewport. If an argument of `true` is supplied or the argument is omitted, the window scrolls so that the top of the element is at the top of the viewport (if possible); otherwise, the element is scrolled so that it is fully visible in the viewport but may not be aligned at the top.
* Force a particular document mode by using the `X-UA-Compatible` HTTP header or by using the `<meta>` tag equivalent:
      <meta http-equiv="X-UA-Compatible" content="IE=IEVersion">
* You can determine the document mode for a given page using the `document.documentMode` property.
* The `contains()` method is called on the ancestor node from which the search should begin and accepts a single argument, which is the suspected descendant node. If the node exists as a descendant of the root node, the method returns `true`; otherwise it returns `false`
* `compareDocumentPosition()` could also determine node relationships, it returns a bitmask indicating the relationship.
* Scrolling:
  1. `scrollIntoViewIfNeeded(alignCenter)` => Scrolls the browser window or container element so that the element is visible in the viewport only if it's not already visible; if the element is already visible in the viewport, this method does nothing. The optional `alignCenter` argument will attempt to place the element in the center of the viewport if set to `true`
  2. `scrollByLines(lineCount)`
  3. `scrollByPages(pageCount)`
