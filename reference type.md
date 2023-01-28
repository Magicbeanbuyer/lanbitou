#go 

Reference types in [[Go]] are the set of slice, map, channel, interface, and function types. 

When you declare a variable from one of these types, the value that’s created is called a _header_ value. 

All header values contain a [[pointer]] to an underlying data structure. 

Each reference type also contains a set of unique fields that are used to manage the underlying data structure. You never share reference type values because the header value is designed to be **copied**. 

![[reference_type.png]]