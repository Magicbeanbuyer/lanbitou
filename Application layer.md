#network 
client software applications are not part of the application layer; rather the application layer is responsible for the protocols and data manipulation that the software relies on to present meaningful data to the user.

Application layer protocols include [[HTTP]] as well as SMTP (Simple Mail Transfer Protocol is one of the protocols that enables email communications).!

![](https://www3.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_Steps.png)
- An HTTP client sends a request message to an HTTP server.  The server, in turn, returns a response message.
- HTTP is a _pull protocol_
- HTTP is a stateless protocol. In other words, the current request does not know what has been done in the previous requests.
- Whenever you issue a URL from your browser to get a web resource using HTTP, e.g. `http://www.nowhere123.com/index.html`, the browser turns the [[URL]] into a _request message_ and sends it to the HTTP server. The HTTP server interprets the request message, and returns you an appropriate response message, which is either the resource you requested or an error message. This process is illustrated below: