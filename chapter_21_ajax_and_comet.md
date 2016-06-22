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
