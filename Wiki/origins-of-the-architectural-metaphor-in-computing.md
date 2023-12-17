https://ieeexplore.ieee.org/document/8356188

- SIGARCH (which explicitly references this metaphor) - founded in 1971 under the [[acm]]

The architectural metaphor represents a shift in the [[history-of-computing]]. Things are more about the user now:
> Computer architecture, like other architecture, is the art of determining the needs of the user of a structure and then designing to meet those needs as effectively as possible within economic and technological constraints [Brooks quoted in the paper]

> Computers, said Eliot Noyes in 1957, “should not be like a ranch house. They should be like a Mies house. They should have that much integrity and joy.” ... Like the houses designed by the great modernist architect Mies van der Rohe, computers could (and should) attain “integrity and joy” through the “expression of structure.”6 ... Mies achieved structural expression by exposing his buildings’ structural beams, rather than hiding them behind drywall and crown moldings, or echoing them in external elements

> Noyes is really making a claim for the elevation of IBM’s new computing machinery from the level of a tool (a means), like a typewriter or a file cabinet, to a culturally meaningful artifact in itself. He is making a place for the computing machine in the overall project of mid-century modernism

> Hellige traces the growth and development of the architectural metaphor over a longer time period and concludes that it has become “a universal concept [Universalbegriff] for every superordinate structuring, style formation and design philosophy” in information technology

That is, just like the [[computational-metaphor]] became the universal concept for society, architecture became the universal concept for tech. We *build* and *architect* programs, no longer just write them.

But Noyes encountered a difficulty when trying to adopt Miesian techniques to computer design. The principles of operation involved in a computer are at the quantum level and are thus imperceptible to humans - exposing these mechanism (e.g. showing bare PCBs) has no meaning to users. Instead, they adopted a 'furnace' approach - only the parts of operation that are *meaningful* to users would be exposed. One example of this is the [[terminal-emulator]], or the register set of a CISC computer - these things are *analogies* to the underlying implementation, not true representations.