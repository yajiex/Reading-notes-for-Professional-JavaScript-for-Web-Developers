# Chapter 13: Events

* Inside an event handler, the `this` object is always equal to the value of `currentTarget`, whereas `target` contains only the actual target of the event.
* Any event that can be canceled using `preventDefault()` will have its `cancelable` property set to true
* The `<img>` element need not be added to the document for the image download to begin; it begins as soon as the `src` property is set.
* Unlike images, JavaScript files start downloading only after the `src` property has been assigned and the element has been added into the document
* Several Focus events:
  1. `blur` => Fires when an element has lost focus. This event doesn't bubble
  2. `focus` => Fires when an element has received focus. This event doesn't bubble
  3. `focusin` => Fires when an element has received focus. This is a bubbling version of the `focus` HTML event
  4. `focusout` => Fires when an element has lost focus. This is a generic version of the `blur` HTML event
* When focus is moved from one element to another on the page, the following order of events is followed:
  1. `focusout` => fires on the element losing focus.
  2. `focusin` => fires on the element receiving focus.
  3. `blur` => fires on the element losing focus.
  4. `DOMFocusOut` => fires on the element losing focus.
  5. `focus` => fires on the element receiving focus.
  6. `DOMFocusIn` => fires on the element receiving focus.
* Several mouse events:
  1. `click` => Fires when user clicks the primary mouse button or when the user presses the Enter key. A `click` event can be fired only if a `mousedown` event is fired and followed by a `mouseup` event on the same element
  2. `mouseenter` => Fires when the mouse cursor is outside of an element and then the user moves it outside of that element's boundaries. This event does not bubble and does not fire when cursor moves over descendant elements
  3. `mouseleave` => Fires when the mouse cursor is over an element and then the user moves it outside of that element's boundaries. This event does not bubble and does not fire when the cursor moves over descendant elements
  4. `mouseout` => Fires when the mouse cursor is over an element and then the user moves it over another element. The element moved to may be outside of the bounds of the original element or a child of the original element. 
  5. `mouseover` => Fires when the mouse cursor is outside of an element and then the user first moves it inside of the boundaries of the element. 
* The order is 
  1. `mouserdown`
  2. `mouseup`
  3. `click`
  4. `mousedown`
  5. `mouseup`
  6. `click`
  7. `dbclick`
* A `click` event can be fired only if a `mousedown` event is fired and followed by a `mouseup` event on the same element
* The DOM provides information about related elements via the `relatedTarget` property on the `event` object. This property contains a value only for the `mouseover` and `mouseout` events; it is `null` for all other events.
* For mouse events, `detail` contains a number indicating how many times a click has occurred at the given location. Clicks are considered to be a `mousedown` event followed by a `mouseup` event at the same pixel location. The value of detail starts at 1 and is incremented every time a click occurs. If the mouse is moved between `mousedown` and `mouseup`, then `detail` is set back to 0.
* Three keyboard events:
  1. `keydown` => Fires when the user presses a key on the keyboard and fires repeatedly while the key is being held down.
  2. `keypress` => Fires when the user presses a key on the keyboard that results in a character and fires repeatedly while the key is being held down. This event also fires for the `Esc` key.
  3. `keyup` => Fires when the user releases a key on the keyboard.
* When the user presses a character key once on the keyboard, the `keydown` event is fired first, followed by the `keypress` event, followed by the `keyup` event. Note that both `keydown` and `keypress` are fired before any change has been made to the text box, whereas the `keyup` event fires after changes have been made to the text box. If a character key is pressed and held down, `keydown` and `keypress` are fired repeatedly and don't stop until the key is released.
* There is only one text event and it is called `textInput`. This event is an augmentation of `keypress` intended to make it easier to intercept text input before being displayed to the user. The `textInput` event fires just before text is inserted into a text box. Since the `textInput` event is interested primarily in characters, it provides a `data` property on the `event` object that contains the character that was inserted (not the character code). The value of `data` is always the exact character that was inserted, so if the `S` key is pressed without `Shift`, data is `"s"`, but if the same key is pressed holding `Shift` down, then data is `"S"`.
* Difference between `keypress` and `textInput`: 
  1. `keypress` fires on any element that can have focus but `textInput` fires only on editable areas
  2. `textInput` fires only for keys that result in a new character being inserted, whereas `keypress` fires for keys that affect text in any way (including `Backspace`).
* There are three composition events:
  1. `compositionstart` => Fires when the text composition system of the IME is opened, indicating that input is about to commence.
  2. `compositionupdate` => Fires when a new character has been inserted into the input field.
  3. `compositionend` => Fires when the text composition system is closed, indicating a return to normal keyboard input.
* When a composition event fires, the target is the input field receiving the text. The only additional event property is `data`, which contains one of the following:
  1. When accessed during `compositionstart`, contains the text being edited (for instance, if text has been selected and will now be replaced).
  2. When accessed during `compositionupdate`, contains the new character being inserted.
  3. When accessed during `compositionend`, contains all of the input entered during this composition session.
* The mutation events defined in DOM Level 2 are as follows:
  1. `DOMSubtreeModified` => Fires when any change occurs to the DOM structure. This is a catchall event that fires after any of the other events fire.
  2. `DOMNodeInserted` => Fires after a node is inserted as a child of another node.
  3. `DOMNodeRemoved` => Fires before a node is removed from its parent node.
  4. `DOMNodeInsertedIntoDocument` => Fires after a node has been inserted either directly or by inserting the subtree in which it exists. This event fires after `DOMNodeInserted`.
  5. `DOMNodeRemovedFromDocument` => Fires before a node is removed either directly or by having the subtree in which it exists removed. This event fires after `DOMNodeRemoved`.
  6. `DOMAttrModified` => Fires when an attribute has been modified.
  7. `DOMCharacterDataModified` => Fires when a change is made to the value of a text node.
* When a node is removed from the DOM using `removeChild()` or `replaceChild()`, the `DOMNodeRemoved` event is fired first. The target of this event is the removed node, and the `event.relatedNode` property contains a reference to the parent node. At the point that this event fires, the node has not yet been removed from its parent, so its `parentNode` property still points to the parent (same as `event.relatedNode`). This event bubbles, so the event can be handled at any level of the DOM. If the removed node has any child nodes, the `DOMNodeRemovedFromDocument` event fires on each of those child nodes and then on the removed node. This event doesn’t bubble, so an event handler is called only if it’s attached directly to one of the child nodes. The target of this event is the child node or the node that was removed, and the event object provides no additional information. After that, the `DOMSubtreeModified` event fires. The target of this event is the parent of the node that was removed. The event object provides no additional information about this event.
* When a node is inserted into the DOM using `appendChild()`, `replaceChild()`, or `insertBefore()`, the `DOMNodeInserted` event is fired first. The target of this event is the inserted node, and the `event.relatedNode` property contains a reference to the parent node. At the point that this event fires, the node has already been added to the new parent. This event bubbles, so the event can be handled at any level of the DOM. Next, the `DOMNodeInsertedIntoDocument` event fires on the newly inserted node. This event doesn’t bubble, so the event handler must be attached to the node before it is inserted. The target of this event is the inserted node, and the event object provides no additional information. The last event to fire is `DOMSubtreeModified`, which fires on the parent node of the newly inserted node.
* Each object that supports the `readystatechange` event has a `readyState` property that can have one of the following five possible string values:
  1. `uninitialized` => The object exists but has not been initialized.
  2. `1loading` => The object is loading data.
  3. `loaded` => The object has finished loading its data.
  4. `interactive` => The object can be interacted with but it’s not fully loaded.
  5. `complete` => The object is completely loaded.
* back-forward cache (bfcache) is designed to speed up page transitions when using the browser’s Back and Forward buttons. The cache stores not only page data but also the DOM and JavaScript state, effectively keeping the entire page in memory. If a page is in the bfcache, the load event will not fire when the page is navigated to.
* `pageshow`, fires whenever a page is displayed, whether from the bfcache or not. On a newly loaded page, `pageshow` fires after the `load` event; on a page in the bfcache, `pageshow` fires as soon as the page's state has been completely restored. The event handler must be attached to `window`. The `event` object for `pageshow` includes a property called `persisted`. This is a Boolean value that is set to `true` if the page is stored in the bfcache or false if the page is not.
* `pagehide`, fires immediately before the `unload` event. `persistent` is set to `true` if the page will be stored in the bfcache once unloaded.
* `hashchange` event handler must be attached to the `window`
* 