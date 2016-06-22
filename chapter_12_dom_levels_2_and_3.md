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
* Several properties for `StyleSheet`, with the exception of `disabled`, the rest are read-only
  1. `disabled` => A Boolean value indicating if the style sheet is disabled. This property is read/write, so setting its value to true will disable a style sheet.
  2. `href` => The URL of the style sheet if it is included using `<link>`; otherwise, this is `null`.
  3. `media` => A collection of media types supported by this style sheet.
  4. `ownerNode` => Pointer to the node that owns the style sheet
  5. `parentStyleSheet` => When a style sheet is included via `@import`, this is a pointer to the style sheet that imported it.
  6. `title` => The value of the title attribute on the `ownerNode`.
* `CSSStyleSheet` also supports:
  1. `cssRules` => collection of rules contained in the style sheet.
  2. `ownerRule` => If the style sheet was included using `@import`, this is a pointer to the rule representing the import; otherwise, this is `null`.
  3. `deleteRule(index)` => Deletes the rule at the given location in the `cssRules` collection.
  4. `insertRule(rule, index)` => Inserts the given string rule at the position specified in the `cssRules` collection.
* The list of style sheets available on the `document` is represented by `document.styleSheets`
* The DOM specifies a property called `sheet` that contains the `CSSStyleSheet` object.
* Several properties for `CSSRule`, which represents each rule in a style sheet
  1. `cssText` => Returns the text for the entire rule.
  2. `parentRule` => If this rule is imported, this is the import rule; otherwise, this is `null`.
  3. `parentStyleSheet` => The style sheet that this rule is a part of.
  4. `selectorText` => Returns the selector text for the rule.
  5. `style` => A `CSSStyleDeclaration` object that allows the setting and getting of specific style values for the rule. It is read-only, whereas `style.cssText` may be overwritten.
  6. `type` => A constant indicating the type of rule.
* Offset dimensions incorporate all of the visual space that an element takes up on the screen, including all padding, scrollbars, and borders (but not including margins), the following four properties are used to retrieve offset dimensions:
  1. `offsetHeight` => The amount of vertical space, in pixels, taken up by the element, including its height, the height of a horizontal scrollbar (if visible), the top border height, and the bottom border height.
  2. `offsetLeft` => The number of pixels between the element’s outside left border and the containing element’s inside left border.
  3. `offsetTop` => The number of pixels between the element’s outside top border and the containing element’s inside top border.
  4. `offsetWidth` => The amount of horizontal space taken up by the element, including its width, the width of a vertical scrollbar (if visible), the left border width, and the right border width.
* The `offsetLeft` and `offsetTop` properties are in relation to the containing element, which is stored in the `offsetParent` property. The `offsetParent` may not necessarily be the same as the `parentNode`. For example, the `offsetParent` of a `<td>` element is the `<table>` element that it’s an ancestor of, because the `<table>` is the first element in the hierarchy that provides dimensions.
* Client dimensions comprise the space occupied by the element's content and its padding. The `clientWidth` property is the width of the content area plus the width of both the left and the right padding. The `clientHeight` property is the height of the content area plus the height of both the top and the bottom padding. The `clientWidth` property is the width of the content area plus the width of both the left and the right padding. The `clientHeight` property is the height of the content area plus the height of both the top and the bottom padding.
* The four scroll dimension properties are as follows:
  1. `scrollHeight` => The total height of the content if there were no scrollbars present.
  2. `scrollLeft` => The number of pixels that are hidden to the left of the content area. This property can be set to change the scroll position of the element.
  3. `scrollTop` => The number of pixels that are hidden in the top of the content area. This property can be set to change the scroll position of the element.
  4. `scrollWidth` => The total width of the content if there were no scrollbars present.
* When trying to determine the total height of a document, including the minimum height based on the viewport, you must take the maximum value of `scrollWidth/clientWidth` and `scrollHeight/clientHeight` to guarantee accurate results across browsers.
* The `scrollLeft` and `scrollTop` properties can be used either to determine the current scroll settings on an element or to set them.
* A new instance of `NodeIterator` can be created using the `document.createNodeIterator()` method. The two primary method of `NodeIterator` are `nextNode()` and `previousNode()`, `nextNode()` returns `null` when it has reached the end of the DOM subtree. `document.createNodeIterator()` method accepts the following four arguments:
  1. `root` => The node in the tree that you want to start searching from.
  2. `whatToShow` => A numerical code indicating which nodes should be visited. It's a bitmask that determines which node to visit by applying one or more filters.
  3. `filter` => A `NodeFilter` object or a function indicating whether a particular node should be accepted or rejected.
  4. `entityReferenceExpansion` => A Boolean value indicating whether entity references should be expanded. This has no effect in HTML pages, because entity references are never expanded.
* `TreeWalker` is a more advanced version of `NodeIterator`. It has the same functionality, including `nextNode()` and `previousNode()`, and adds the following methods to traverse a DOM structure in different directions:
  1. `parentNode()` => Travels to the current node’s parent.
  2. `firstChild()` => Travels to the fi rst child of the current node.
  3. `lastChild()` => Travels to the last child of the current node.
  4. `nextSibling()` => Travels to the next sibling of the current node.
  5. `previousSibling()` => Travels to the previous sibling of the current node.
* When used with a `TreeWalker` object, `NodeFilter.FILTER_SKIP` skips over the node and goes on to the next node in the subtree, whereas `NodeFilter.FILTER_REJECT` skips over that node and that node’s entire subtree.
* The ·TreeWalker· type also has a property called ·currentNode· that indicates the node that was last returned from the traversal via any of the traversal methods. This property can also be set to change where the traversal continues from when it resumes
* `document.createRange()`, several properties for `Range` type:
  1. `startContainer` => The node within which the range starts (the parent of the first node in the selection).
  2. `startOffset` => The offset within the `startContainer` where the range starts. If `startContainer` is a text node, comment node, or `CData` node, the `startOffset` is the number of characters skipped before the range starts; otherwise, the offset is the index of the first child node in the range.
  3. `endContainer` => The node within which the range ends (the parent of the last node in the selection).
  4. `endOffset` => The offset within the `endContainer` where the range ends (follows the same rules as `startOffset`).
  5. `commonAncestorContainer` => The deepest node in the document that has both `startContainer` and `endContainer` as descendants.
* The simplest way to select a part of the document using a range is to use either `selectNode()` or `selectNodeContents()`. These methods each accept one argument, a DOM node, and fill a range with information from that node. The `selectNode()` method selects the entire node, including its children, whereas `selectNodeContents()` selects only the node’s children.
* When `selectNode()` is called, `startContainer`, `endContainer`, and `commonAncestorContainer` are all equal to the parent node of the node that was passed in, the `startOffset` property is equal to the index of the given node within the parent’s childNodes collection
* When `selectNodeContents()` is called, `startContainer`, `endContainer`, and `commonAncestorContainer` are equal to the node that was passed in, the `startOffset` property is always equal to 0, since the range begins with the first child of the given node, whereas `endOffset` is equal to the number of child nodes (`node.childNodes.length`).
* It’s possible to get more fine-grained control over which nodes are included in the selection by using the following range methods:
  1. `setStartBefore(refNode)`
  2. `setStartAfter(refNode)`
  3. `setEndBefore(refNode)`
  4. `setEndAfter(refNode)`
* Creating complex ranges requires the use of the `setStart()` and `setEnd()` methods. Both methods accept two arguments: a reference node and an offset. For `setStart()`, the reference node becomes the `startContainer`, and the offset becomes the `startOffset`. For `setEnd()`, the reference node becomes the `endContainer`, and the offset becomes the `endOffset`.
* `deleteContents()` simply deletes the contents of the range from the document, the range selection process altered the underlying DOM structure to remain well formed
* `extractContents()` also removes the range selection from the document, it returns the range's document fragement as the function value.
* When a document fragment is passed into `appendChild()`, only the fragment’s children are added, not the fragment itself
* `cloneContents()` can be used to create a clone of range, the document fragement returned by `cloneContents()` contains clones of the nodes contained in the range instead of the actual nodes.
* The splitting of nodes ensures that a well-formed document isn’t produced until one of these methods is called. The original HTML remains intact right up until the point that the DOM is modified.
* The `insertNode()` method enables you to insert a node at the beginning of the range selection.
* `surroundContents()` method accepts one argument, which is the node that surrounds the range contents. Behind the scenes, the following steps are taken:
  1. The contents of the range are extracted (similarly to using `extractContents()`).
  2. The given node is inserted into the position in the original document where the range was.
  3. The contents of the document fragment are added to the given node.
* You can collapse a range by using the `collapse()` method, which accepts a single argument: a Boolean value indicating which end of the range to collapse to. If the argument is `true`, then the range is collapsed to its starting point; if it is `false`, the range is collapsed to its ending point. To determine if a range is already collapsed, you can use the `collapsed` property
* You can use the `compareBoundaryPoints()` method to determine if the ranges have any boundaries (start or end) in common. The method accepts two arguments: the range to compare to and how to compare
* `detach()` method detaches the range from the document on which it was created
