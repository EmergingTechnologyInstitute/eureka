
ETI Fork Details
================

The purpose of this fork is to make Eurkea work with other Cloud providers. The two problems we found during porting, where around DNS and Name Resolution.

* When configuring Eureka to use DNS configuration, Eureka relies on multi-line DNS TXT records. This isn't supported on either of the DNS providers we had access to. We modified the code to use a space delimitted list, and to remove surrounding double quotes. Both of these changes are compatiable when used with a DNS provier which does support multiple text records.
* The original implementation relied on the local hostname and domain be resolvable to an IP address.  This isn't necessarily the case with every cloud provider, so we changed the code to register the private IP address as opposed to the domain name and host.

Eureka
======

Eureka is a REST (Representational State Transfer) based service that is primarily used in the AWS cloud for locating services for the purpose of load balancing and failover of middle-tier servers.

At Netflix, Eureka is used for the following purposes apart from playing a critical part in mid-tier load balancing.

* For aiding Netflix Asgard - an open source service which makes cloud deployments easier, in  
    + Fast rollback of versions in case of problems avoiding the re-launch of 100's of instances which 
      could take a long time.
    + In rolling pushes, for avoiding propagation of a new version to all instances in case of problems.

* For our cassandra deployments to take instances out of traffic for maintenance.

* For our memcached caching services to identify the list of nodes in the ring.

* For carrying other additional application specific metadata about services for various other reasons.


Support
----------
[Eureka Google Group] (https://groups.google.com/forum/?fromgroups#!forum/eureka_netflix)


Documentation
--------------
Please see [wiki] (https://github.com/Netflix/eureka/wiki) for detailed documentation.
