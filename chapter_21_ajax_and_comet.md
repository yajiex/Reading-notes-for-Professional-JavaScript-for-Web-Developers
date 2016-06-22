# Chapter 21: Ajax and Comet
* To begin using an XHR object, you will first call the method `open()`, which accepts three arguments: the type of request to be sent ("get", "post", and so on), the URL for the request, and a Boolean value indicating if the request should be sent asynchronously. The URL is relative to the page on which the code is called, although an absolute path can be given as well. The call to `open()` does not actually send the request; it simply prepares a request to be sent. You can access only URLs that exist on the same origin, which means the same domain, using the same port, and with the same protocol. If the URL specifies any of these differently than the page making the request, a security error is thrown.
* The status code of 304 indicates that a resource hasn't been modified and is being served from the browser's cache, which also means a response is available
* The XHR object has a `readyState` property that indicates what phase of the request/response cycle is currently active. The possible values are as follows:
  1. `0` => Uninitialized. The `open()` method hasn't been called yet.
  2. `1` => Open. The `open()` method has been called but `send()` has not been called.
  3. `2` => Sent. The `send()` method has been called but no response has been received.
  4. `3` => Receiving. Some response data has been retrieved.
  5. `4` => Complete. All of the response data has been retrieved and is available.
* You can cancel an asynchronous request before a response is received by calling the `abort()` method
* You can retrieve the response headers from an XHR object by using the `getResponseHeader()` method and passing in the name of the header to retrieve. It's also possible to retrieve all headers as a long string by using the `getAllResponseHeaders()` method.
* The `onprogress` event listener receives an `event` object whose target is the XHR object and contains three additional properties: `lengthComputable`, a Boolean indicating if progress information is available; `position`, which is the number of bytes that have already been received; and `totalSize`, which is the total number of expected bytes as defined by the `Content-Length` response header.
* There are some additional limitations on a cross-domain XHR object that are necessary for security purposes. They are as follows:
  1. Custom headers cannot be set using `setRequestHeader()`.
  2. Cookies are neither sent nor received.
  3. The `getAllResponseHeaders()` method always returns an empty string.
* There are two popular approaches to Comet: long polling and streaming.
  1. Long polling => The page initiates a request to the server and the server holds that connection open until it has data to send. Once the data is sent, the connection is closed by the browser and a new connection is immediately opened up to the server. This process continues for as long as the page is open in the browser.
  2. HTTP streaming => The browser sends a request to the server and the server holds that connection open, periodically sending data through the connection to the server.
* 
