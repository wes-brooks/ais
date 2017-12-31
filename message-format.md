message format:

1. Preamble (training sequence): 28 bits This segment consists of alternating ones and zeros (0101 . . . ) and the sequence can either start with a “1” or a “0” since NRZI encoding is used [9]

2. Start flag: The start flag is 8 bits long and consists of a standard HDLC flag (01111110), marking the start of each transmission packet.

3. data: The data portion is 168 bits long in the default transmission packet. 

4. Frame check sequence: 16-bit cyclic redundancy check (CRC) polynomial to calculate the checksum as defined in ISO/IEC 3309: 1993 [9]. The CRC bits are preset to ”1” at the beginning of the CRC calculation. Only the data portion is included in the checksum calculation
5. End flag: The end flag is 8 bits long and identical to the start flag.
6. Buffer: The buffer is normally 24 bits long and is used to compensate for bit stuffing, distance delays, repeater delay and synchronisation jitter [9].

Notes:

- The total length of the normal packet is 256 bits, which is equivalent to one TDMA time slot.

- the message is grouped into bytes first and the least significant bits are output first. During the output process, data should be subject to bit-stuffing and NRZI coding [9]. Unused bits in the last byte should be set to zero in order to preserve the boundary of the bytes.

- are the padding bits in the last byte added before or after LSBing?

- Bit stuffing
  + If five consecutive ones are encountered on the output bit stream to be transmitted, a zero should be inserted.
  + The main reason for bit-stuffing is to prevent the transmitter from transmitting a data sequence that is identical to the start or stop flag.
  + Bit stuffing applies to all bits except the start flag, stop flag and the training sequence [9].
  + Bit stuffing happens AFTER conversion of the message to 8-bit LSB bytes

-When data is output on the VHF data link it should be grouped in bytes of 8 bits from top to bottom of the table associated with each message in accordance with ISO/IEC 3309: 1993. Each byte should be output with least significant bit first. During the output process, data should be subject to bit-stuffing and NRZI coding as described in § 3.2.2.