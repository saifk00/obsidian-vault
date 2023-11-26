# Advanced Microcontroller Bus Architecture

Introduced by ARM in 1996, the Advanced Microcontroller Bus Architecture (AMBA) is a set of specifications for interconnect protocols between functional blocks in a digital hardware system. Altera has a competing standard called [[avalon]] which is proprietary.

# History
The first AMBA busses were Advanced System Bus (ASB) and Advanced Peripheral Bus (APB).

In 1999, they added AMBA High-performance Bus (AHB).

In 2003, [[axi-protocol]] was added along with the Advanced Trace Bus (ATB) that supported debug/trace stuff.

In 2010, AMBA 4 introduced AXI4 followed shortly by the [[memory-coherency]] extension **AXI Coherency Extensions** (ACE).

Since these standards are all free, they are the de factor standard for processor bus architectures.

# AMBA 1: ASB and APB
ASB is the core, high performance backbone of the original AMBA spec. The CPU and other bus masters (e.g. DMA controllers, high speed memory) are connected to this bus. A bridge connects the ASB to an APB.

The APB is a simpler, low-speed low-power bus. It is used to connect things like I/O ports, UART, timers, etc.

Placing peripherals on the APB lowers the load on ASB thus increasing its performance.

# AMBA 2: ASB APB AHB
AHB became the *backbone bus*, superseding ASB. ASB became an alternative for AHB if the high-performance of AHB is not required. APB is compatible with both ASB and AHB. for a deep dive see [[amba-2-deep-dive]].

# References
[Original 1996 AMBA Intro](https://developer.arm.com/documentation/dvi0010/a)
[1999 AMBA 2 Spec](https://developer.arm.com/documentation/ihi0011/a/)
