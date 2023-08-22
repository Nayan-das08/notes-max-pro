- before namespaces, the above mentioned names competed for slots in *global namespace*
	- because of this, many conflicts arose
	- eg: for a user-defined function `abs()` overriding the standard library function `abs()` 
## solution
- **namespace**: localizes the names of identifies to avoid *name collisions*
- allows same name *to be used in different contexts*
- before: entire C++ library was defined within the global namespace (the only namespace then)
- now: C++ library is defined within its own namespace `std`