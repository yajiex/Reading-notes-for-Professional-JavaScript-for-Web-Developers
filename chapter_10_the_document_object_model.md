# Chapter 10: The Document Object Model

* Every node has a `nodeType` property that indicates the type of node that it is.
* `NodeList` objects are actually queries being run against the DOM structure, so changes will be reflected in `NodeList` objects automatically.
* The `ownerDocument` property is a pointer to the document node that represents the entire document.
* If the node passed into `appendChild()` is already part of the document, it is removed from its previous location and placed at the new location.
* The `cloneNode()` method doesn't copy JavaScript properties that you add to DOM nodes, such as event handlers. This method copies only attributes and, optionally, child nodes. Everything else is lost.
* `documentElement` property always points to the `<html>` element in an HTML page.
* 
