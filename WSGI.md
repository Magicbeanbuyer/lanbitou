#python #web

![python-wsgi-app](https://res.cloudinary.com/practicaldev/image/fetch/s--Aozu6gS4--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/56zf2r5ljmujm2jwtz8y.jpg)

A Web Server Gateway Interface (WSGI) server implements the web server side of the WSGI interface for running Python web applications.

A traditional web server does not understand or have any way to run Python applications.

Serving thousands of requests for dynamic content at once is the domain of WSGI servers, not frameworks. WSGI servers handle processing requests from the web server and deciding how to communicate those requests to an application framework's process

![WSGI Server - Web server - Browser](https://www.fullstackpython.com/img/visuals/web-browser-server-wsgi.png)

![WSGI server invoking a WSGI application.](https://www.fullstackpython.com/img/visuals/wsgi-interface.png)