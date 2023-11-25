Introduced in 2003 as part of [[amba]], the Advanced Extensible Interface (AXI) protocol is a bus protocol for on-chip communication.

# Main Features
There are five main *channels* each of which is associated with a letter prefix (just like [[amba-2-deep-dive|AMBA 2]]) has multiple *signals*.
1. Write Address **AW**
2. Write Data **W**
3. Write Response **B**
4. Read Address **AR**
5. Read Data **R**

- Separate read and write channels means that reads and writes may occur at the same time
- Managers can submit transactions without waiting for earlier ones to complete
- No strict timing relationship between {AW, W} or {AR, R}
- Unaligned data transfers for data sizes larger than 8 bits
- Out of order transaction completion - each transaction has an ID
- Burst transactions - subordinates will compute addresses based on starting address

# Channel Transactions
