# Chapter 10: The Document Object Model

* Every node has a `nodeType` property that indicates the type of node that it is.
* `NodeList`, `NamedNodeMap` objects are actually queries being run against the DOM structure, so changes will be reflected in `NodeList` objects automatically.
* The `ownerDocument` property is a pointer to the document node that represents the entire document.
* If the node passed into `appendChild()` is already part of the document, it is removed from its previous location and placed at the new location.
* The `cloneNode()` method doesn't copy JavaScript properties that you add to DOM nodes, such as event handlers. This method copies only attributes and, optionally, child nodes. Everything else is lost.
* `documentElement` property always points to the `<html>` element in an HTML page.
* `var doctype = document.doctype; // get reference to <!DOCTYPE>`
* Changing the value of the `title` property does not change the `<title>` element at all.
* `document.domain` can never be set to a domain that the URL doesn't contain. Pages from different subdomains can't communicate with one another via JavaScript because of cross-domain security restrictions. By setting `document.domain` in each page to the same value, the pages can access `JavaScript` objects from each other. A further restriction in the browser disallows tightening of the `domain` property once it has been loosened.
* `HTMLCollection` object has an method `namedItem`, that lets you reference an item in the collection via its `name` attribute. You can also access named items by using bracket notation.
* To retrieve all elements in the document, pass in `"*"` to `getElementsByTagName()`.
* Special Collections:
  1. `document.anchors` => Contains all `<a>` elements with a `name` attribute in the document.
  2. `document.forms` => Contains all `<form>` elements in the document.
  3. `document.images` => Contains all `<img>` elements in the document.
  4. `document.links` => Contains all `<a>` elements with an `href` attribute in the document.
* The `document.implementation` property is an object containing information and functionality tied directly to the browser's implementation of the DOM. `var hasXmlDom = document.implementation.hasFeature("XML", "1.0");`
* Even though the following code looks correct, the closing `"</script>"` string is interpreted as matching the outermost `<script>` tag. To avoid this, you simply need to change the string as `"<\/script>"`
      <html>
      <head></head>
      <body>
        <script type="text/javascript">
          document.write("<script></script>");
        </script>
      </body>
      </html>
* If `document.write()` is called after the page has been completely loaded, the content overwrites the entire page. Neither `open()` nor `close()` is required to be used when `write()` or `writeln()` is used during the course of page loading.
* Every HTML element `HTMLElement` has a property `dir`, indicates the direction of the language, `"ltr"` or `"rtl"`
* When `normalize()` is called on a parent of two or more text nodes, those nodes are merged into one text node whose `nodeValue` is equal to the concatenation of the `nodeValue` properties of each text node.
* The `splitText()` method splits a text node into two text nodes, separating the `nodeValue` at a given offset. The method returns the new text node, which has the same `parentNode` as the original.
