# Chapter 23: Offline Applications and Client-Side Storage
* HTML5 defines a `navigator.onLine` property that is `true` when an Internet connection is available or `false` when it's not. 
* HTML5 defines two events to better track when the network is available or not: `online` and `offline`. Each event is fired as the network status changes from online to offline or vice versa respectively.
* The server sends a `Set-Cookie` HTTP header containing session information as part of any response to an HTTP request. Browsers store such session information and send it back to the server via the Cookie HTTP header for every request after that point
* When a cookie is set, it is sent along with requests to the same domain from which it was created.
* Cookies are made up of the following pieces of information stored by the browser:
  1. `Name` => A unique name to identify the cookie. Cookie names are case-insensitive
  2. `Value`
  3. `Domain` => This value can include a subdomain (such as www.wrox.com) or exclude it (such as .wrox.com, which is valid for all subdomains of wrox .com). If not explicitly set, the domain is assumed to be the one from which the cookie was set.
  4. `Path` => The path within the specified domain for which the cookie should be sent to the server
  5. `Expiration` => By default, all cookies are deleted when the browse session ends; however, it's possible to set another time for the deletion. Cookies can be deleted immediately by setting an expiration date that has already occurred
  6. `Secure flag` => When specified, the cookie information is sent to the server only if an SSL connection is used.
* Setting `document.cookie` does not overwrite any cookies unless the name of the cookie being set is already in use.
* There is also a type of cookie called `HTTP-only`. `HTTP-only` cookies can be set either from the browser or from the server but can be read only from the server, because JavaScript cannot get the value of `HTTP-only` cookies.
* The `sessionStorage` object stores data only for a session, meaning that the data is stored until the browser is closed. This is the equivalent of a session cookie that disappears when the browser is closed. Data stored on `sessionStorage` persists across page refreshes and may also be available if the browser crashes and is restarted, depending on the browser vendor.
* In order to access the same `localStorage` object, pages must be served from the same domain (subdomains aren't valid), using the same protocol, and on the same port.
* 
