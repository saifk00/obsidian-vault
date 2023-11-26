[Intro to AMBA AXI](https://developer.arm.com/documentation/102202/0300)

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
- Out of order transaction completion - each **transaction** has an ID
- Burst transactions - subordinates will compute addresses based on starting address

# Channel Transfers and Transactions
In a channel, the *source* and *destination* perform a ready/valid handshake like so:

```
Source - valid -> Dest
Source <- ready - Dest
```

The source/dest of a transaction depends on which channel we're in. For example, in **AR**, the manager is the source while the subordinate is the destination. A **transfer** is a single exchange of information, with *one* handshake. A transfer completes in the cycle where the valid and ready signals are both high on the rising clock edge. A **transaction** is a burst of transfers.

To prevent deadlocking - sources cannot wait for READY to assert VALID, but destinations can wait for VALID before asserting READY.

There are three burst types: fixed, wrapping, and incrementing. Fixed is often used for reading FIFOs while wrapping can be used for ring buffers. Incrementing is the usual.

