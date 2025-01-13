Link: https://www.gobeyond.dev/encoding-binary/

- 16bits is 2 bytes
- 32bits is 4 bytes
- big endian - most significant byte first, as in how we read numbers left to right
	- e.g. 1016 in hex is 0x03F8, which is `03 F8` in big endian encoding
	- often referred to as _network byte order_
- little endian - least significant byte first
	- e.g. 1016 in hex is 0x03F8, which is `F8 03` in little endian encoding
	- the benefit here is being able to increase the memory allocation of a value without changing the memory address, e.g.
		- `F8 03` - 2 bytes
		- `F8 03 0 0` - 4 bytes