# TCP Header

- source port
- destination port: 80
- sequence number: 4000 (with size 500, you send 4000-4499) 
- acknowledgement number: last byte recv + 1  (it will be 4500 then)
- window: flow control window (how much buffer the recv has)
- Control bit: U (urgent - let's get to the application quickly), P (push), 
A (Ack) is gnerally set to 1 except the first packet to initiate the connection
S (Syn) the first packet is sent woth S=1 A=0 so that it synchronize the seqno.
--- setting seqno. to 0 is vulnerable
F (Fin) no more data to send
Offset (the offset data begins - sometimes you have "option" bytes that is padded before the data)