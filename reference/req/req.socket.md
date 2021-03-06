# `req.socket`

If the current request (`req`) originated from a connected Socket.IO client, `req.socket` refers to the raw Socket.IO socket instance.

### Usage

```usage
req.socket;
```


### Details

> **Warning:**
>
> `req.socket` may be deprecated in a future release of Sails.  You should use the [`sails.sockets.*`](https://sailsjs.com/documentation/reference/Sockets) methods instead.

If the current request (`req`) did NOT originate from a Socket.IO client, `req.socket` does not have the same meaning.  In the most common scenario&mdash;HTTP requests&mdash;`req.socket` _exists_, but it refers instead to the underlying TCP socket. Before using `req.socket`, you should check the [`req.isSocket`](https://sailsjs.com/documentation/reference/request-req/req-is-socket) flag to ensure the request arrived via a connected Socket.IO client.

`req.socket.id` is a unique identifier representing the current socket.  This is generated by the Socket.IO server when a client first connects and is a valid unique identifier until the socket is disconnected (if the client is a web browser, for example, `req.socket.id` would be valid until the user closes their browser tab).

Sails also provides direct, low-level access to all other methods and properties of a Socket.IO `Socket`, including `req.socket` and its methods `req.socket.join`, `req.socket.leave`, `req.socket.broadcast`, etc.  Check out the relevant [Socket.IO docs](https://socket.io/docs/rooms-and-namespaces/#Rooms) for more information.


### Example

```js
if (req.isSocket) {
  // Low-level Socket.io methods and properties accessible on req.socket.
  // ...
}
else {
  // This is not a request from a Socket.io client, so req.socket
  // may or may not exist.  If this is an HTTP request, req.socket is actually
  // the underlying TCP socket.
  // ...
}
```






<docmeta name="displayName" value="req.socket">
<docmeta name="pageType" value="property">

