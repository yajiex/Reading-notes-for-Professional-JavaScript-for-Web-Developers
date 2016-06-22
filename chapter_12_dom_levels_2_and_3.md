# Chapter 12: DOM Levels 2 and 3
* Namespace are specified using the `xmlns` attribute. You can explicitly create a prefix for an XML namespace using `xmlns`, followed by a colon, followed by the prefix.
* The `Node` type evolves in DOM Level 2 to include the following namespace-specific properties:
  1. `localName` => The node name without the namespace prefix
  2. `namespaceURI` => The namespace URI of the code or `null` if not specified
  3. `prefix` => The namespace prefix or `null` if not specified
* DOM Level 3 goes one step further and introduces the following methods to work with namespaces:
  1. `isDefaultNamespace(namespaceURI)` => Returns `true` when the specified `namespaceURI` is the default namespace for the node
  2. `lookupNamespaceURI(prefix)` => Returns the namespace URI for the given `prefix`
  3. `lookupPrefix(namespaceURI)` => Returns the prefix for the given `namespaceURI`
* The `Document` type is changed in DOM Level 2 to include the following namespace-specific methods:
  1. `createElementNS(namespaceURI, tagName)` => Creates a new element with the given `tagName` as part of the namespace indicated by `namespaceURI`
  2. `createAttributeNS(namespaceURI, attributeName)` => Creates a new attribute node as part of the namespace indicated by `namespaceURI`
  3. `getElementsByTagNameNS(namespaceURI, tagName)` => Returns a `NodeList` of elements with the given `tagName` that are also a part of the namespace indicated by `namespaceURI`
* The purpose of `importNode()` is to take a node from a different document and import it into a new document so that it can be added into the document structure. Remember, every node has an `ownerDocument` property that indicates the document it belongs to. If a method such as `appendChild()` is called and a node with a different `ownerDocument` is passed in, an error will occur. Calling `importNode()` on a node from a different document returns a new version of the node that is owned by the appropriate document.
* `defaultView` is a pointer to the window (or frame) that owns the given document.
* 

