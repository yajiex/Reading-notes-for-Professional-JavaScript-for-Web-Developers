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
  2. 