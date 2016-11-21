# Consistent Hashing

Consistent hashing was first introduced by David Kager and others in the excellent paper
titled
   "Consistent Hashing and Random Trees: Distributed Caching Protocols for Relieving Hot
   Spots on the World Wide Web"


## Why do we care ?

The need for consistent hashing arose from limitations experienced when running a collection
of machines to distribute the load - for example, caches. A common way to load balance is
to compute hash on an object and place the object on cache machine number ObjHash % n, 
where 'n' is the number of cache machines. However, this has the limitation where, if a
machine is added or removed, 'n' changes, consequently, the lookup logic breaks and all
requests are routed to the backing server, until the cache rebuilds again.


## How does consistent hasing help ?

The basic idea behind the algorithm is to hash both objects and caches using the same
hash fn. The reason to do this is to map the cache to an interval, which will contain
a number of object hashes. If the cache is removed, then its interval is taken over by
a cache with the adjacent interval. All the other caches remain unchanged. 

More details [here](http://www8.org/w8-papers/2a-webserver/caching/paper2.html)


