# Reliable Communication Retransmission

- Go-back-N (pessimistic): all N are re-transmitted
- Selective Repeat (optmisitic): if time out on #x, just re-send #x
- Why would you wanna do go-back N then ?
- well you don't know if there is a burst of loss (in this casee go-back-N does it in one go, i.e., better recovery speed for significant error)
- Example 1: Sender window = N, Recv window = 1 ... the system behaves like ... Go-Back-N !
- Example 2: Sender window = N, Recv window = N ... the system behaves like ... Selective Repeat (it can buffer)
- when implementing, do not aggressive re-transmit. Some of them may get buffered in the recv already. The lower seqno. may be lost (and only one of that).