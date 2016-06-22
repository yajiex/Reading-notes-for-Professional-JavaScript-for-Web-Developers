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
* By default, the `<input>` element displays a text box, even when the `type` attribute is omitted (the default value is `"text"`). The `size` attribute can then be used to specify how wide the textbox should be in terms of visible characters. The `maxlength` attribute specifies the maximum number of characters allowed in the text box
* `select()` selects all of the text in a text box. Most browsers automatically set focus to the text box when the `select()` method is called
* The `select` event fires once the user has finished selecting text. The `select` event also fires when the `select()` method is called.
* `selectionStart` and `selectionEnd` contain zero-based numbers indicating the text-selection boundaries (the offset of the beginning of text selection and the offset of end of text selection, respectively).
* `setSelectionRange()` takes two arguments: the index of the first character to select and the index at which to stop the selection
* The following six events are related to the clipboard:
  1. `beforecopy` => Fires just before the copy operation takes place.
  2. `copy` => Fires when the copy operation takes place.
  3. `beforecut` => Fires just before the cut operation takes place.
  4. `cut` => Fires when the cut operation takes place.
  5. `beforepaste` => Fires just before the paste operation takes place.
  6. `paste` => Fires when the paste operation takes place.
* The `beforecopy`, `beforecut`, and `beforepaste` events give you the opportunity to change the data being sent to or retrieved from the clipboard before the actual event occurs. However, canceling these events does not cancel the clipboard operation — you must cancel the `copy`, `cut`, or `paste` event to prevent the operation from occurring.
* There are three methods on the `clipboardData` object: `getData()`, `setData()`, and `clearData()`.
* Any field marked as `required` must have a value in order for the form to be submitted.
* The `pattern` attribute was introduced for text fields in HTML5. This attribute specifies a regular expression with which the input value must match. Note that `^` and `$` are assumed at the beginning and end of the pattern, respectively. Specifying a `pattern` does not prevent the user from entering invalid text. The `pattern` is applied to the value, and the browser then knows if the value is valid or not.
* You can check if any given field on the form is valid by using the `checkValidity()` method
* You can instruct a form not to apply any validation to a form by specifying the `novalidate` attribute. If there are multiple submit buttons in a form, you can specify that the form not validate when a particular submit button is used by adding the `formnovalidate` attribute to the button itself
* `HTMLSelectElement` type provides the following properties and methods in addition to those that are available on all form fi elds:
add(newOption, relOption) — Adds a new <option> element to the control before the
related option.
multiple — A Boolean value indicating if multiple selections are allowed; equivalent to the
HTML multiple attribute.
options — An HTMLCollection of <option> elements in the control.
remove(index) — Removes the option in the given position.
selectedIndex — The zero-based index of the selected option or –1 if no options are
selected. For select boxes that allow multiple selections, this is always the fi rst option in
the selection.
size — The number of rows visible in the select box; equivalent to the HTML size attribute.