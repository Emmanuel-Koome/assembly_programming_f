# Subtraction and EFLAGS

Both programs were assembled as 32-bit ELF binaries, run successfully, and inspected in GDB immediately after the `SUB` instruction. The flags below are `CF` (borrow for subtraction), `PF` (even parity), `AF` (borrow from bit 4), `ZF` (zero), `SF` (sign), and `OF` (signed overflow).

## `sub1.asm`

`AL = 50 - 80 = -30`, represented as the 8-bit result `0xE2`.

- Set: `CF`, because unsigned 50 is less than 80 and the subtraction borrows; `PF`, because `0xE2` has four set bits; and `SF`, because the result's top bit is 1.
- Cleared: `AF`, because the low-nibble subtraction `2 - 0` needs no borrow; `ZF`, because the result is nonzero; and `OF`, because `-30` is representable as a signed 8-bit value.

## `sub2.asm`

`AX = 1000 - 2000 = -1000`, represented as the 16-bit result `0xFC18`.

- Set: `CF`, because unsigned 1000 is less than 2000 and the subtraction borrows; `PF`, because the low result byte `0x18` has two set bits; and `SF`, because bit 15 is 1.
- Cleared: `AF`, because the low-nibble subtraction `8 - 0` needs no borrow; `ZF`, because the result is nonzero; and `OF`, because `-1000` is representable as a signed 16-bit value.