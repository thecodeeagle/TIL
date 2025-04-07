# HTTP and HTTP Requests

So many scenarios in our daily life require us sending/receiving HTTP requests, especially when dealing with logging infrastructure.
I decided to do a deep dive today.

## HTTP
Just the name, is a protocol. Primary purpose is fetching HTML documents.
Client-server protocol - which means - requests are originated by the recipient.
However, a stream of data is not passed, client-server communication happens through exchange of multiple individual messages.

 - Sent by the client -> called **"request"**
 - Sent by the server -> called **"response"**

### Request Methods

So naturally, we have some functionality to request stuff, some different methods defined by the protocol itself. Also called HTTP **verbs**. Found these useful, more you can find at https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods

 1. `GET`: requests a representation of the required resource. Should not include any content.
 2. `HEAD`: Identical to `GET`, but does not ask for the response body.
 3. `POST`: submits an entity to the specified resource, often causing a change in state or side effects on the server.
 4. `CONNECT`: establishes a tunnel to the server identified by the target resource.

### Headers
The HTTP headers allow the client and server to pass additional information along with the requests and responses. Formats and conventions dependent on the HTML version you are using.

While we have request headers and response headers typically detailing size, auth and stuff, one interesting section I found was **Representation headers.** Basically, they describe how to interpret the data contained in the message. Pretty useful stuff.

They allow the underlying data to be extracted and understood. The underlying resource is semantically the same in each case, but its representation is different.

An interesting point I came across: Clients specify the formats that they prefer to be sent during [Content Negotiation](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Content_negotiation) (using `Accept-*` headers), and the representation headers tell the client **the format of the _selected representation_ they received.**

Another is **Content Headers**, they describe the content of the body of an HTTP message, after any message framing in the body has been removed. They specifically describe the properties of the [message content](https://developer.mozilla.org/en-US/docs/Glossary/HTTP_Content) that is conveyed in a particular message _as it is transported_, such as the length of the content, the transport encoding, which part of the resource is carried in the data (for multi-part messages), and message integrity checks. They differ from the [Representation headers](https://developer.mozilla.org/en-US/docs/Glossary/Representation_header), which describe the encoding, media type, language, and other characteristics of the resource, and allow the underlying data to be interpreted.