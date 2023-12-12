[[x86-architecture]]
While the 30286 introduced [[x86-protected-mode]], the 386 introduced in 1985 added *paging*.

Unlike the 286, 386 was a 32-bit processor. At long last, it had as many address pins as its internal bus; 32 bits each for a 4GiB physical address space. In practice, main memory was not yet 4GiB but this was what the programmer saw.

Segmentation was now achieved with 16-bit selectors and 32 bit offsets, thus increasing the maximum segment size from  64KiB to 4GiB.

Segment bases were now 32 bits, with a 20-bit limit field. This can provide a limit of up to 4GiB through use of the 'granularity' flag, which indicates the limit field refers to 4KiB chunks rather than byte.

Now, the segmentation unit forms a linear address by taking the segment base, adding the offset, and checking the limit. This is not the end though, as 30386 had the optional **paging** feature.

Unlike segments, pages are of fixed size - a 4KiB (=2^12 byte) chunk of contiguous physical memory. Linear addresses issued by the segmentation unit are interpreted as follows:
- 10 bits indexing into a *page directory* to select a page table
- 10 bits indexing into the *page table* to select a page
- 12 bits as an offset into the page

A page table is a list of 32-bit page identifiers (i.e. their base addresses). Since the page directory lists up to 1024 page tables, and each page table lists up to 1024 pages, a page directory contains up to 2^20 pages. Each page contains 2^12 bytes, so the page directory maps the entire physical address space (2^20 * 2^12 = 2^32).

The CPU has a register PDBR containing the current page directory.