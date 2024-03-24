The direction in which bytes in memory are read - akin to English being read left to write, and Arabic being read right to left

![[Decimal-number_--1-.png]]

Required for data to be effectively communicated between different systems

- refers only to the order of bytes, bits are always read left to right
- only significant for multi-byte values - a single byte is read the same whether big or little endian
- big-endian, or BE
	- the most significant byte (MSB) is stored at the lowest memory address
	- when multiple bytes are read, the first will be the largest
	- associated mainly with older computer architectures
- little-endian, or LE
	- the least significant byte (LSB) is stored at the lowest memory address

![[MSbyte.png]]


## links and resources

- https://www.freecodecamp.org/news/what-is-endianness-big-endian-vs-little-endian/
