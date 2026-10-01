# Addition and EFLAGS

Both programs were assembled as 32-bit ELF binaries, run successfully, and inspected in GDB immediately after the `ADD` instruction. The flags below are `CF` (carry), `PF` (even parity), `AF` (carry from bit 3 to bit 4), `ZF` (zero), `SF` (sign), and `OF` (signed overflow).

## `add1.asm`

`AL = 120 + 10 = 130`, so the 8-bit result is `0x82`.

- Set: `PF`, because `0x82` has two set bits; `AF`, because the low-nibble addition `8 + 0xA` carries into bit 4; `SF`, because the result's top bit is 1; and `OF`, because adding two positive signed 8-bit values produced a negative signed representation (`130` is greater than `127`).
- Cleared: `CF`, because the unsigned sum fits in 8 bits; `ZF`, because the result is nonzero.

## `add2.asm`

`AX = 32000 + 500 = 32500 = 0x7EF4`.

- Cleared: `CF`, because the unsigned sum fits in 16 bits; `PF`, because the low byte `0xF4` has an odd number of set bits; `AF`, because the low-nibble addition `0 + 4` has no carry; `ZF`, because the result is nonzero; `SF`, because bit 15 is 0; and `OF`, because the positive signed result fits in the 16-bit signed range.