# AMBA 2 Deep Dive
[1999 AMBA 2 Spec](https://developer.arm.com/documentation/ihi0011/a/)

- Bus cycle
	- AHB and APB: rising edge to rising edge
	- ASB: falling edge to falling edge
- ASB transfer sizes: byte, halfword (16b) and word (32b)
	- AHB also supports 64b and 128b transfers
- AHB and ASB support burst mode, APB does not

# Overview of AHB and ASB
Masters control the bus by providing address and control info. Slaves respond to masters based on their address space. The bus arbiter ensures only one master uses the bus at a time. The protocol for arbitration (letting each device know it can use the bus, etc.) is fixed, but the algorithm used to decide on a master is up to the implementer. There is a single centralized decoder that converts addresses into select signals for slaves (slaves do not implement their own logic to detect if they are being addressed).

# Signal Names
Signals are prefixed with a letter that indicates which bus theyre associated with.
H: AHB signal
A: ASB signal for arbiters
B: ASB signal
D: ASB decoder signal
P: APB signal

# ASB in Detail
Flow:
1. Arbiter determines which master gets the bus
2. Master initiates transfers on the bus
3. Decoder uses higher addr bits to select a slave
4. Slave provides transfer response back to master, and the transfer occurs
Masters may lock the bus using the **BLOK** signal during e.g. sequential data transfers. In a burst sequence, the master controls the **BLAST** signal to indicate whether this is the last transfer in the sequence. The slave drives **BWAIT** to indicate if the current transfer can complete. If high, another cycle is required.