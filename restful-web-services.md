# RESTful Web Services - O'Reilly - Leonard Richardson & Sam Ruby


## Chapter 1 - The Programmable Web and Its Inhabitants

### HTTP: Documents in Envelopes
HTTP is a document-based protocol, in which the client puts a document in an envelope and sends it to the server. The server returns the favor by putting a response document in an envelope and sending it to the client. HTTP has strict standards for what the envelopes should look like, but it doesn't much care what goes inside.

_The HTTP method_
- HTTP verb or HTTP action. The name of the method is like a method name in a programming language: it indicates how the client expets the server to process this envelope.

_The path_
The part of the URI to right of the hostname. Is the address on the envelope.

_The request headers_
Bits of metadata: keyvalue pairs that act like informational stickers slapped onto the envolope.

_The entity-body_
Also called document or representation. The content inside the envelope.

The HTTP Response can be divided into three parts:

_The HTTP Response code_
This is a numeric code that tells the client whether its request went well or poorly.

_The response headers_
Just as with the reques headers, these are informational stickers.

_The entity-body_
Content.

### Method Information
How the server knows what to do with the data. the five most common HTTP methods are GET, HEAD, PUT, DELETE, and POST. This is enough to distinguish between “retrieve some data” (GET), “delete that same data” (DELETE), and “overwrite it with different data” (PUT).

