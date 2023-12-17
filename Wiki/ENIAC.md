The Electronic Numerical Integrator and Computer

Ceremonially switched on by [[gladeon-barnes]] of the Ordnance department who owned the machine (!) [[ceruzzi-2003]]@20


# Facts
Its programming manual was written by [[adele-goldstine]]

It was permanently installed in Aberdeen, Maryland at the Ballistics Research Laboratory [[ceruzzi-2003]]

# The New York Times Article
On Feb 15, 1946, the New York Times published a front-page story "Electronic Computer Flashes Answers, May Speed Engineering" about the unveiling of the ENIAC

> "Army ordnance men had been on the lookout for a machine with which to prepare a large volume of ballistic data, which in turn was needed to break a threatened bottleneck in the production of firing and bombing tables for new offensive weapons going overseas. Without the tables the guns could not be used effectively" [NYT Feb 15, 1942, page 16]

> "A very difficult wartime problem" was sent through its intricate circuits soon after it was completed. The Eniac completed the task in two hours. Had it not been available the job would have kept busy 100 trained men for a whole year

The operating frequency of the ENIAC was 100KHz, and 5000instructions/second
> It does [arithmetic] by generating very accurately timed electrical impulses at a speed of 100,000 per second. And can do one operation every twentieth pulse

**This is technically incorrect**: [table 1.1 of the ENIAC report](https://ftp.arl.army.mil/ftp/historic-computers/drawings/big-px-1-421.gif) shows that the operating time for an *addition* is 20 pulses, but other operations require some multiple of this value.

As for its cost
> More than 200,000 man0hours went into the building of the machine.
> It contains mroe than half a million soldered joints, and cost about $400,000
> Three times as much electricity is required to operate it as for one of our largest broadcasters - 150kW

The scientist questioned, Dr. John Mauchly, seemed to be more interested in more quotidian things than 'difficult wartime problems':
> better weather-predicting, [...] airplanes, gas turbines, microwave radio tubes, television [...]

Interestingly, there is no concept of a 'programmer' or a 'program', just that the problem at hand needs to be reduced to its component arithmetic by someone and punched into the card.
# ENIAC Report
https://ftp.arl.army.mil/~mike/comphist/46eniac-report/
- Clock operated at 100kHz
- "Addition time" - the time to complete 1 addition = 20 pulses (1/5000 of a second)
> The units of the ENIAC can be classified functionally into 4 categories: arithmetic, memory, input and output, and governing
- 20 accumulators (add/sub), 1 multiplier 1 divider, 1 sqrt
- Separate data and instruction memories! [[harvard-architecture]]

