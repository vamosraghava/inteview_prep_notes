
# HTTP and HTTPS Protocols

## References

[HTTP 1](https://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-1--net-31177)

[HTTP 2](https://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-2--net-31155)

## Key Notes

 - Stateless Protocol
 - Sits in Application Layer of OSI Networking Reference Layer
 - Runs on top of TCP/IP, default port 80
 - HTTPS runs on default port 443. HTTPS has additional TLS or SSL layer in between HTTP and TCP/IP.

### HTTP Connections

 - HTTP Connection is established between Client (IP, Port) and Server
   (IP, Port).
 
 - HTTP 1.0: All connections are closed after a single transaction. 
 - HTTP 1.1 Supports **persistent** connections i.e. long-lived connections, they are kept open until client explicitly asks to close. 
	 - They are default in HTTP 1.1.
	 - Client can explicitly set `'Connection: close'` header if server can
   close connection after sending back response.
   
 - Browsers/Clients also leverage technique '**parallel**' connections,
   to minimize the network delays.

## HTTP Headers

### General Headers

 - All HTTP 1.1 clients are required to accept `Transfer-Encoding: chunked` header. this is used to break the response into smaller parts; Allows streaming of server responses instead of one big payload to client.
 - Via Header is used in TRACE command, and is updated by all intermediate proxies/gateways/routers with its IP
 
 ### Entity Headers
 - Content-* headers (Content-Type, Content-Length, Content-Encoding, Content-Language, Content-Location etc) specify structure, encoding, and size of message. 
	 - some of these headers are applicable when the relevant entity is present in body.
 - Expires, Last-Modified are used to track when the message expires, or was last modified.
 - Custom headers can be created by client, and are treated as entity headers by the HTTP protocol.

### Request format

Request-Line = Method SP URI SP HTTP-Version CRLF
Method = "OPTIONS"
       | "HEAD"  
       | "GET"  
       | "POST"  
       | "PUT"  
       | "DELETE"  
       | "TRACE"

`SP`  is the space separator between the tokens.  `HTTP-Version`  is specified as  _"HTTP/1.1"_  and then followed by a new line. Thus, a typical request message might look like:

    GET /articles/http-basics HTTP/1.1
    Host: www.articles.com
    Connection: keep-alive
    Cache-Control: no-cache
    Pragma: no-cache
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8

`From`, `Host`, `Referer` and `User-Agent` identify details about the client that initiated the request. The `If-` prefixed headers are used to make a request more conditional, and the server returns the resource only if the condition matches

### Response Format

The response format is similar to the request message, except for the status line and headers. The status line has the following structure:

    Status-Line = HTTP-Version SP Status-Code SP Reason-Phrase CRLF

-   HTTP-Version is sent as  `HTTP/1.1`
-   The Status-Code is one of the many statuses discussed earlier.
-   The Reason-Phrase is a human-readable version of the status code.

A typical status line for a successful response might look like so:

HTTP/1.1 200 OK

The response headers are also fairly limited, and the full set is given below:

     response-header = Accept-Ranges
                     | Age
                     | ETag              
                     | Location          
                     | Proxy-Authenticate
                     | Retry-After       
                     | Server            
                     | Vary              
                     | WWW-Authenticate

-   `Age`  is the time in seconds since the message was generated on the server.
-   `ETag`  is the MD5 hash of the entity and used to check for modifications.
-   `Location`  is used when sending a redirection and contains the new URL.
-   `Server`  identifies the server generating the message.

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjU2MDY3NjMyLDgyMzk1Mjc5NywtMTk5Mz
M2NDAyMywxMjk4OTU2OTY3LDIyMTMzMTU0LC00MjcyMDQ5OV19

-->