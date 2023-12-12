The 80286, released in 1982, came with two modes: real mode, which essentially mimicked the 8086 for backwards compatibility (albeit with higher performance), and the "native" *protected* mode. This mode allowed for a 24-bit *physical* address space and 30-bit *virtual* (linear) address space.

A virtual address contains two parts: a 16 bit *segment selector* and an *offset*.

the selector component contains 14 bits to denote a segment, where one bit is interpreted as the *Table indicator bit* (the other two bits are used for protection - rings 0 to 3). The table indicator splits the virtual memory into two halves: global and local address space. The global space is used for OS software, library routines, etc. So the total virtual memory that a process sees is 2^14 segments big, but half of them are 'global' segments used for accessing things that are shared across tasks

The other 13 bits are an *index* into a segment descriptor table. This is some data that lives in main memory which helps map virtual addresses to physical ones. Segment descriptor tables represent a mapping of virtual memory to the physical memory present at the CPU's address pins. It contains a number of segment *descriptors*, which contain the base address of the given segment. This is added to the 16-bit offset value to generate the physical address.

There are two types of segment descriptor tables; the one *global* GDT, and a per-task *local* LDT. Each may contain up to 2^13 =8192 entries to accomodate for the 13-bit index part of the segment selector component. 

Segment descriptor tables themselves are segments; ones with a size of 8192 to be precise. Since theres only one GDT, its base is stored in a single register, GDTR. LDTR is another register that stores the current LDT segment

The LDT lies within the *global address space* - this prevents tasks from modifying/reading their own LDT to get physical address info!

Each segment descriptor contains:
- 2 bytes denoting the size of the segment (0 to 2^16=64K bytes)
	- This is distinct from real mode segments which dont have a fixed size; this is to ensure that invalid accesses result in a fault
- 3 bytes (24 bits) denoting the physical base address of the segment
	- This is what the 16-bit offset gets added to; hence why the physical address space is only 24 bits
- 1 byte for access controls
- 2 reserved bytes

The six bytes for size, base, and access are cached by the hardware alongside the four active segments (CS SS DS ES) so that the 24-bit physical addresses can be quickly generated any time the 16-bit offset value is updated. Basically, any instruction will implicitly reference one of these segments along with its own 16-bit offset. The 16 bit segment register contain the *selector* (which, as you will recall, contains index + TI + 2 protection bits), which normally needs to go out to main memory to fetch the base + size of the segment, but caching keeps these values alongside the register so actually all that happens is that the 16 bit offset is added to the cached base and compared with the size limit value before being sent onto the address pins.


http://bitsavers.org/components/intel/80286/210498-005_80286_and_80287_Programmers_Reference_Manual_1987.pdf
https://web.archive.org/web/20070622205752/http://www.internals.com/articles/protmode/introduction.htm