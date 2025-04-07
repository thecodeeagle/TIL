# HTTP and HTTP Requests

So many scenarios in our daily life require us sending/receiving HTTP requests, especially when dealing with logging infrastructure.
I decided to do a deep dive today.

## HTTP
Just the name, is a protocol. Primary purpose is fetching HTML documents.
Client-server protocol - which means - requests are originated by the recipient.
However, a stream of data is not passed, client-server communication happens through exchange of multiple individual messages.

 - Sent by the client -> called **"request"**
 - Sent by the server -> called **"response"**