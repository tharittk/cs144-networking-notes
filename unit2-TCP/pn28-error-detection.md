# Error Detection

- Checksum, CRC, MAC
- [---data--- | ED] <- you append/prepend the Error-detection value
- checksum is fast to compute. But weak. If two bit error cancel each other, checksum cannot detect it.
- CRC: Cyclic Redundancy (link layer uses this) 
- MAC: Massege Authenticator Code - not as good as CRC - guarantee with probability
- IP Checksum: 2-complement arithmatic -> wrap-around, add 1, flip bit
- 16-bit CRC. distill n bits of data into c bits, detect any error <= c-bit long
- polynomial long division, Message M, padded to G length, do M div by G (generator polynomial)
- G determines the error detection strength
- MAC: crytography-based, c = MAC(M, secret), hard to calculate c if does not have s. very hard to generate M whose MAC is C
- not as good for error detection. MAC cannot guarantee (never 100%)
- error detection promise very little (cannot guarantee many edge cases). But in practice, it is good enugh