# Chapter 14: Scripting Forms
* `HTMLFormElement` has the following additional properties and methods:
  1. `acceptCharset` => The character sets that the server can process; equivalent to the HTML `accept-charset` attribute.
  2. `action` => The URL to send the request to; equivalent to the HTML `action` attribute.
  3. `elements` => An `HTMLCollection` of all controls in the form.
  4. `enctype` => The encoding type of the request; equivalent to the HTML `enctype` attribute.
  5. `length` => The number of controls in the form.
  6. `method` => The type of HTTP request to send, typically `"get"` or `"post"`; equivalent to the HTML `method` attribute.
  7. `name` => The name of the form; equivalent to the HTML `name` attribute.
  8. `reset()` => Resets all form fields to their default values.
  9. `submit()` => Submits the form.
  10. `target` => The name of the window to use for sending the request and receiving the response; equivalent to the HTML `target` attribute.
* Image buttons are defined using the `<input>` element with a type attribute of `"image"`
* When a form is submitted by pressing `Enter` on the keyboard while a `form` control has focus, the `submit` event fires right before the request is sent to the server. This gives you the opportunity to validate the form data and decide whether to allow the form submission to occur. Preventing the event's default behavior cancels the form submission
* When a form is submitted via `submit()`, the submit event does not fire, so be sure to do data validation before calling the method.
* Reset buttons are created using either the `<input>` or the `<button>` element with a type attribute of `"reset"`. When a form is reset by the user clicking a reset button, the `reset` event fires. `reset()` fires the reset event the same as if a reset button were clicked.
* HTML5 introduces an `autofocus` attribute for form fields that causes supporting browsers to automatically set the focus to that element without the use of JavaScript
* For `<input>` and `<textarea>` elements, the `change` event fires when the field loses focus and the value has changed since the time the control got focus. For `<select>` elements, however, the change event fires whenever the user changes the selected option; the control need not lose focus for change to fire.