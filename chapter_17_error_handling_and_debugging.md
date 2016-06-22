# Chapter 17: Error Handling and Debugging
* It's very important to understand that any return statements in either the `try` or the `catch` portion will be ignored if a `finally` clause is also included in your code.
* When the `throw` operator is used, code execution stops immediately and continues only if a trycatch statement catches the value that was thrown.
* An `onerror` event handler doesn't create an `event` object in any browser, instead, it receives three arguments: the error message, the URL on which the error occurred, and the line number.
* Images also support an `error` event. Any time the URL in an image's src attribute doesn't return a recognized image format, the error event fires.

