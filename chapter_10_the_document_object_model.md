# Chapter 10: The Document Object Model

* Every node has a `nodeType` property that indicates the type of node that it is.
* `NodeList` objects are actually queries being run against the DOM structure, so changes will be reflected in `NodeList` objects automatically.
* The `ownerDocument` property is a pointer to the document node that represents the entire document.
* If the node passed into `appendChild()` is already part of the document, it is removed from its previous location and placed at the new location.
* The `cloneNode()` method doesn't copy JavaScript properties that you add to DOM nodes, such as event handlers. This method copies only attributes and, optionally, child nodes. Everything else is lost.
* `documentElement` property always points to the `<html>` element in an HTML page.
* `var doctype = document.doctype; // get reference to <!DOCTYPE>`
* Changing the value of the `title` property does not change the `<title>` element at all.
* `document.domain` can never be set to a domain that the URL doesn't contain. Pages from different subdomains can't communicate with one another via JavaScript because of cross-domain security restrictions. By setting `document.domain` in each page to the same value, the pages can access `JavaScript` objects from each other. A further restriction in the browser disallows tightening of the `domain` property once it has been loosened.
* `HTMLCollection` object has an method `namedItem`, that lets you reference an item in the collection via its `name` attribute. You can also access named items by using bracket notation.
* To retrieve all elements in the document, pass in `"*"` to `getElementsByTagName()`.
* 
