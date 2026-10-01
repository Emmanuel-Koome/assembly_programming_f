# Multiplication and EFLAGS

Both programs were assembled as 32-bit ELF binaries, run successfully, and inspected in GDB immediately after the unsigned `MUL` instruction. For `MUL`, `CF` and `OF` are set when the upper half of the double-width product is nonzero, and cleared when it is zero. The other arithmetic status flags (`PF`, `AF`, `ZF`, and `SF`) are undefined by the instruction, so their debugger display cannot be reported as a meaningful set or cleared result.

## `mul1.asm`

`AL = 25`; multiplying by byte `10` produces `AX = 250 = 0x00FA`. The upper half of the product (AH) is zero, so `CF` and `OF` are cleared.

## `mul2.asm`

`AX = 3000`; multiplying by word `200` produces `DX:AX = 0x0009:0x27C0` (600,000). The upper half (DX) is nonzero, so `CF` and `OF` are set.