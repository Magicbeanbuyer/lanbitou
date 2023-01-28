Uniform Resource Locator
`protocol://hostname:port/path-and-file-name`
`http://www.nowhere123.com/docs/index.html`

There are 4 parts in a URL:

1.  _Protocol_: The application-level protocol used by the client and server, e.g., HTTP, FTP, and telnet.
2.  _Hostname_: The DNS domain name (e.g., `www.nowhere123.com`) or IP address (e.g., 192.128.1.2) of the server.
3.  _Port_: The TCP port number that the server is listening for incoming requests from the clients. When a client issues a URL without explicitly stating the port number, e.g., `http://www.nowhere123.com/docs/index.html`, the browser will connect to the default port number 80 of the host `www.nowhere123.com`. You need to explicitly specify the port number in the URL, e.g. `http://www.nowhere123.com:8000/docs/index.html` if the server is listening at port 8000 and not the default port 80.
4.  _Path-and-file-name_: The name and location of the requested resource, under the server document base directory, e.g. `/docs/index.html`.


