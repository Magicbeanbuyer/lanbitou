gRPC can use [[protobuf]]s as both its Interface Definition Language (**IDL**) and as its underlying message interchange format. 

defining a service, specifying the methods that can be called remotely with their parameters and return types

In gRPC, a [[client]] application can directly call a method on a server application on a different machine as if it were a local object.



![Concept Diagram](https://grpc.io/img/landing-2.svg)


On the server side, the server implements this interface and runs a gRPC server to handle client calls. 
 
On the client side, the client has a stub (referred to as just a client in some languages) that provides the same methods as the server.

A gRPC **channel** provides a connection to a gRPC server on a specified host and port. 


### Read More
[How to write a gRPC client in Python for a gRPC service written in Java - Stack Overflow](https://stackoverflow.com/a/61787478/5720958)





