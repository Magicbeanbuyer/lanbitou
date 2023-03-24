#go 

![[Screenshot 2023-01-31 at 15.31.33.png]]

context is used to control cancellation through timeout & deadlines, to store key value pairs
transport layer: handle incoming requests, create a context and populate the context with a trace_id or request_id
business layer: business logic

purpose:
- monitoring
- control cancellation: control how long parts of our code is allowed to execute
 