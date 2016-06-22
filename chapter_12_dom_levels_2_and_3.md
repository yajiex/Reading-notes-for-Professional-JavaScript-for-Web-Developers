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
* The DOM Level 2 HTML module also adds a method called `createHTMLDocument()` to `document.implementation`. The purpose of this method is to create a complete HTML document, including the `<html>`, `<head>`, `<title>`, and `<body>` elements. This method accepts a single argument, which is the title of the newly created document (the string to go in the `<title>` element)
* `isSupported()` indicates what the node is capable of doing, it accepts two arguments: the feature name and the feature version.
* DOM Level 3 introduces two methods to help compare nodes: `isSameNode()` and `isEqualNode()`. Both methods accept a single node as an argument and return true if that node is the same as or equal to the reference node. Two nodes are the same when they reference the same object. Two nodes are equal when they are of the same type and have properties that are equal (`nodeName`, `nodeValue`, and so on), and their attributes and `childNodes` properties are equivalent (containing equivalent values in the same positions).
* The `setUserData()` method assigns data to a node and accepts three arguments: the key to set, the actual data (which may be of any data type), and a handler function. The handler function for `setUserData()` is called whenever the node with the data is cloned, removed, renamed, or imported into another document. The handler function accepts five arguments: a number indicating the type of operation (1 for clone, 2 for import, 3 for delete, or 4 for rename), the data key, the data value, the source node, and the destination node. The source node is null when the node is being deleted, and the destination node is `null` unless the node is being cloned.
* For Frames and iframes, `contentDocument` contains a pointer to the `document` object representing the contents of the frame. Access to the `document` object of a frame or iframe is limited based on cross-domain security restrictions.
* When in standards mode, all measurements have to include a unit of measure, like `"20px"`
* Several properties for `style` object:
  1. `length` => The number of CSS properties applied to the element.
  2. `getPropertyCSSValue(propertyName)` => Returns a CSSValue object containing the value of the given property.
  3. `getPropertyPriority(propertyName)` => Returns `“important”` if the given property is set using `!important`; otherwise it returns an empty string.
  4. `getPropertyValue(propertyName)` => Returns the string value of the given property.
  5. `removeProperty(propertyName)` => Removes the given property from the style.
* `getPropertyCSSValue()` returns a `CSSValue` object that has two properties: `cssText` and `cssValueType`. The `cssText` property is the same as the value returned from `getPropertyValue()`. The `cssValueType` property is a numeric constant indicating the type of value being represented: 0 for an inherited value, 1 for a primitive value, 2 for a list, or 3 for a custom value.
* Removing a property using `removeProperty()` means that any default styling for that property (cascading from other style sheets) will be applied.
* The `style` object offers information about the `style` attribute on any element that supports it but contains no information about the styles that have cascaded from style sheets and affect the element.
* `getComputedStyle()` accepts two arguments: the lement to get the computed style for and a pseudo-element string (such as `":after"`)
* 

