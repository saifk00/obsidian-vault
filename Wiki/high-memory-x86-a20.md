Oh boy do I have a story for you.

Okay, so in 1978, Intel introduced the [[8086]] processor. It had 20 bits of physical address space (that is, physical address pins A0...A19) despite it being a 16-bit CPU, to address the then-standard 1MiB of external memory. 

But you cant fit 20 bits of address into a 16 bit register. The natural solution is to use two registers, but only use 4 bits of one of them. Intel called this __segmentation__. The *segment* register holds the highest 16 bits of the address, to which we _add_ the 16-bit offset value.
$$
\text{address} = (\text{segment} \lt\lt 4) + \text{offset}
$$

- [ ] can you actually find the architecture diagram for the 8086 to show _where_ address comes from? is it plugged into some memory circuit?

Intuitively, for a given segment register value, varying `offset` lets us address $2^{16}$ different bytes. So we can visualize this addressing scheme as separating memory into chunks which we will (duh) call _segments_, each of which is $2^{16}$ bytes (aka 64KiB) long.
- [ ] How many segments are there?
- [ ] Describe how there might be multiple addresses for the same physical address

Lets play with this for a second - what happens if you set them both to the maximum `0xFFFF` ? applying the formula, we get `0xFFFF0 + 0xFFFF = 0x10FFEF`... Hold on, that is actually a bit more than the maximum 20 bit address of `0xFFFFF` ... In fact, its almost a whole segment (64KiB) bigger. This extra bit of memory is called "high memory". No problem, lets just drop the most significant bit!

Another thing to mention: at the time, memory mapped IO was not standard, and so the instruction set had the concept of [[8086-io-space]] (actually, they did have memory mapped IO in the sense that the external memory could have regions that mapped to some piece of hardware - the CPU wouldn't know the difference after all).

Fast forward to literally 1984: the IBM Personal Computer AT (PC-AT for short) is released to the public. It was built around the 8086's successor - the 8086 2. Wait no, scratch that - 80**2**86. Why not. Released 4 years after its predecessor, the 80286 made the huge upgrade of providing a whopping 24 bits of external address pins!

Hold on. x86 is always backwards compatible right? So what about that wraparound behavior? Programs that generate an address of `0x10FFEF` are expecting to access the same memory as `0xFFEF` - this is no good with the larger 24 bit space since we dont wrap around! So, to get around this, they disabled the 21st address bit (A20) by default. But now new programs need to manually enable A20. How?

Well. Theres this [keyboard controller](https://wiki.osdev.org/%228042%22_PS/2_Controller) sitting at addresses `0x0060-0x0064` in the I/O space. And it had an extra pin, so the designers decided what the hell, lets just wire the A20 enable bit to that! So to turn on A20, you enable bit 1 in a write command to address `0x0064`, usually using the value `0xDDFF` (bit 1 corresponds to A20, bit 0 actually resets the CPU (!))