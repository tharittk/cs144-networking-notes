# Life of a Packet

- TCP Byte Strea: "3-way handshake"
- Client -> Server: synchronize "SYN"
- Server -> Client: syn and ack "SYN/ACK"
- Client -> Server: "ACK"
- network layer address (ip_addr, tcp_port): packet leaving the same computer (ip_addr) looks the same, so we need the port
- the tcp port tells "which application to deliver this packet to"
- Inside each hop: forwarding table (longest match prefix)
- pattern A -> Link 1
- pattern B -> Link 5
- default = least-specific route
- `$ traceroute -w 1 www.cs.brown.edu`
