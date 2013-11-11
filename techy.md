

### About maxium tcp connection to port,

A single listening port can accept more than one connection simultaneously.

There is a '64K' limit that is often cited, but that is per client per server port, and needs clarifying.

Each TCP/IP packet has basically four fields for addressing; these are:

source_ip source_port destination_ip destination_port
< client            > < server                      >
Inside the TCP stack, these four fields are used as a compound key to match up packets to connections (e.g. file descriptors).

If a client has many connections to the same port on the same destination, then three of those fields will be the same - only source_port varies to differentiate the different connections. Ports are 16-bit numbers, therefore the maximum number of connections any given client can have to any given host port is 64K.

However, multiple clients can each have up to 64K connections to some server's port, and if the server has multiple ports or either is multi-homed then you can multiply that further.

So the real limit is file descriptors. Each individual socket connection is given a file descriptor, so the limit is really the number of file descriptors that the system has been configured to allow and resources to handle. The maximum limit is typically up over 300K, but is configurable e.g. with sysctl.

The realistic limits being boasted about for normal boxes are around 80K for example single threaded Jabber messaging servers.
