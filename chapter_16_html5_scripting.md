# Chapter 16: HTML5 Scripting
* The `postMessage()` method accepts two arguments: a message and a string indicating the intended recipient origin. It is possible to allow posting to any origin by passing in `"*"` as the second argument to `postMessage()`, but this is not recommended.
* A `message` event is fired on a window when an XDM (Cross-document messaging) message is received. The `event` object that is passed to an `onmessage` event handler has three important pieces of information:
  1. `data` => The string data that was passed as the first argument to `postMessage()`.
  2. `origin` => The origin of the document that sent the message
  3. `source` => A proxy for the `window` object of the document that sent the message. This proxy object is used primarily to execute the `postMessage()` method on the window that sent the last message.
* The `dragenter` event (similar to the `mouseover` event) fires as soon as the item is dragged over the drop target. Immediately after the `dragenter` event fires, the `dragover` event fires and continues to fire as the item is being dragged within the boundaries of the drop target. When the item is dragged outside of the drop target, `dragover` stops firing and the `dragleave` event is fired (similar to `mouseout`). If the dragged item is actually dropped on the target, the `drop` event fires instead of `dragleave`. The target of these events is the drop target element.
* If you drag an element over something that doesn't allow a drop, the drop event will never fi re regardless of the user action. However, you can turn any element into a valid drop target by overriding the default behavior of both the `dragenter` and the `dragover` events.
* The `dataTransfer` object has two primary methods: `getData()` and `setData()`.
* 
