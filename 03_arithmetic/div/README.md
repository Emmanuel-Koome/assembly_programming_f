# Division and EFLAGS

Both programs were assembled as 32-bit ELF binaries, run successfully, and inspected in GDB immediately after the unsigned `DIV` instruction. `DIV` does not define the arithmetic status flags `CF`, `PF`, `AF`, `ZF`, `SF`, or `OF`; each is undefined after division. Therefore these flags cannot accurately be described as set or cleared based on the debugger's displayed values. The quotient and remainder, by contrast, are defined in the result registers.

## `div1.asm`

The 16-bit dividend in `AX` is 100 and the 8-bit divisor in `BL` is 7. The quotient is 14 in `AL`, and the remainder is 2 in `AH` (`100 = 14 * 7 + 2`).

## `div2.asm`

The dividend in `DX:AX` is 50,000 and the divisor in `BX` is 300. The quotient is 166 in `AX`, and the remainder is 200 in `DX` (`50000 = 166 * 300 + 200`).