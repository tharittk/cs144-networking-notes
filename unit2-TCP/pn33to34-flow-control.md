# Flow Control

- Problem: sender can send data faster than the receiver can take in
- receiver should send some feedback to sender: Stop and Wait, Sliding Window

### Stop and Wait
- one packet on flight at any time
- Sender sends, receiver sends acknowledgement. Continue.
- Recv FSM: self-loop, Sender FSM: 2 states (wait for data, wait for ACK), timeout = resend
- Example: 1) no loss is easy. 2) data loss triggers timeout, sender resends.
- 3) data is delivered but ACK is loss, sender resend, and recv re-send ACK.
- 4) (Failure) sender -> recv ACK but the ACK arrive too late (after time out) but
- the sender already re-send the data. (process ACK) The sender send another pack as well.
- the 2nd packet is loss. The recv send ACK. Now the sender doesn't know that this ACK
- is the duplicated ACK or from ACK of lost 2nd packet --- Look somewhat like Two-General Problem
- Basic problem: How to detect duplicate
- 1-bit counter: receiver can tell if new data or duplicate (assumption: network does not duplicate packets, packets do not delay for multiple timeout).

### Sliding Window
- major problem of Stop and Wait: underutilize capacity. Say recv can take 10 MB/s, the Round-trip time (1 RT =1 packet #bytes) may cause usage of 2% only
- Sliding window = generalized stop-and-wait: allow multiple un-acked segments
- 12 Kbit / packet, RTT = 20ms. -> Recv can take 10 Mbit/s. = it can take 10 Mb / 20 per RTT -> To saturate, you should send 500 kbit per RTT. 
- so you should have ~ 500 / 12 = 40 packets in sliding window
- SeqNo for each sement
- SWS, LAR, LSS, (+ RWS - recv-side buffer)
- Maintain invariant (Last Segment Send - Last Ack Recv) <= Send Window Size
- i.e., you cannot stretch more than #send window size from what you most recently receive ACK
- TCP acks = next expected data
- Sending cumulative acks: if receives 1, 2, 3, 5 -> acknowledge 3 [I have received everything up to 3 (continous) - not everything it has received]
- Example: receive window = 1 ("go-back-n-protocol" here n = 1)
- send window size = 3.. send 0, 1, 2, .. (0ack)3, (1ack)4,(2)5
- if 3 is loss, it has to discard 4, 5 because recv cannot buffer 4, 5. -> sender has to re-send 4,5 too.
- the sender will be timeout for ACK of 3 -> re-send. If you have recv buffer for 4, 5. Once the resent 3 comes in, recv can ACK 3, 4, 5 at once.
- Information in ther TCP header: 
- there is window field (#bytes), data seqno., acknowledge seqno. (never send data > ack + window)
