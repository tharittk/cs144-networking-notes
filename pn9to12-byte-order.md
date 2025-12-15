# Memory, Byte Order, Packet Formats

- a copy of memory that is passed through a networking card
- endianness: how the program access multi-byte valued memory
- little endian: LSB comes first i.e., the lowest address then
- Quiz:
- width 16, decimal 53, hexadecimal 0x3500 -> 0x35 comes last, 0x00 comes first -> little endian
- width 16, decimal 4116, hex 0x1014 -> 0x10 is 4096 and 0x14 is 20 -> Big endian
- 32 bit, decimal 5, hex 0x0...05 -> Big endian
- 32 bit, 83,886,080, hex 0x0...5 -> it should be 5x2^sth: Little endian
- 32bit, 305,414,945, hex 0x21433412 -> symmetric hex -> ambiguious (WRONG) -> you have odd decimal: 0x12 cannot be the lowest byte (it will make even number) -> MSB comes last: little endian

- Why matter? Two networks comunicating must agree while CPU uses differently ! ARM uses Big Endian
```C
  1 #include <stdio.h>
  2 #include <stdint.h>
  3
  4 int main (void) {
  5     uint16_t val = 0x400;
  6     uint8_t* ptr = (uint8_t*)&val;
  7     printf("Probing low addr of 0x400 ... \n");
  8     if (ptr[0] == 0x40){
  9         printf("It is MSB: Big Endian \n");
 10     } else if (ptr[0] == 0x00){
 11         printf("It is LSB: Little Endian \n");
 12     } else {
 13         printf("unknown endian \n");
 14     }
 15     return 0;
 16 }
```

- All internet communication protocol use big endian. What if you want your computer to be little endian ?
- c provides `ntohs` <- this is for short
- this conerts network-ordered to host-ordered.
- Be carefule whenever you handle the network data !!
- Packet format: RFC 791, IPv4 has 5 lines (4 bytes each) -> 20 bytes of total header
- Wireshark example: Total length = 1230 byte -> in the header shows 04 ce (big endian of 2 bytes - half of the first line of packet header)
- 04 * 256 + 12 * 16 + 14 = 1230
