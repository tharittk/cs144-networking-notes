# IP Address
- the service provider by the internet protocol
- transport sengment [data | hdr] -> goes to [dat | hdr] in datagram (packet)
- IP = datagram service
- [data | IP SA (source address) | DA]
- unreliable (packet might be dropped)
- best-effort (might drop packet if neccesary like full queues)
- why is the IP service designed to be so simple ? -> simple, dump, minimal: Faster, more streamlined and lower cost to build and maintain
- the end-to-end principle: where possible, implement the features in the end host (sender or receiver) -> radical as telelphone puts complexity to the switches (and not the phone)
- allows (variable) reliablity service to build on top (depending on the application needed)
- IP works on any link layer: IP makes very few assumption

### IP service model
- Prevent the packets from looping forever (if routing table dynamically change and caues such behaviors) -> Time-to-live (TTL) - it does not guarantee that looping will not happen (being simple)
- Will fragment packets if they are too long
- use checksum to reduce chance of delivering to the wrong place
- allow for new versions (IPv4 = 32 bit, IPv6 = 128 bit)

### IPv4 Datagram
Destination IP Address
Source IP Address
Protocol ID -> use for multiplexing (6 = TCP segment -> Parse correctly)
version -> IPv4 or IPv6
Time to live "TTL" -> as discussed
Packet ID -> helps keep track if packet need to be broken down
Type of service
Header Length
Checksum
