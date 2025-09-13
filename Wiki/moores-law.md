---
tags: 
author: 
title: 
location:
---
https://web.archive.org/web/20070713083559/http://www.ieee.org/portal/site/sscs/menuitem.f07ee9e3b2a01d06bb9305765bac26c8/index.jsp?&pName=sscs_level1_article&TheCat=2165&path=sscs/06Sept&file=Liddle.xml

Some salient points
- Moore's law is an _economic_ proposition, not a technical one
	- The idea is that the computer industry will consolidate a few architectures (abstracted by things like compilers) which will simulataneously
		- Grow the market for each one; your code need only target x86 to cover 99% of personal computers
		- Amortize investment in a particular program - it will automatically get faster each year as the underlying chip improves
	- This is why there was huge interest in parallel architectures in the 70s, but it has since died off
		- Why invest in redesigning software for these complicated tasks when you can just wait 18 months to double its speed automatically?

Is moore's law dead? Jensen will say yes, Gelsinger will say no. Each is worried about their own bottom line. This is the fundamental question - can we continue to rely on automatic improvements to traditional architectures for code to 'do more stuff'?

Maybe its not dead yet, but it certainly cannot last forever. There is a fundamental quantum limit to traditional MOSFET design that prevents this (i think we are about 2nm away from that?), but perhaps there are radical changes to transistor design that can keep the doubling going (finfets? alternative materials? 3d stacking?).

In reality, **nothing is forever**. the real interesting question to me is, *once* Moore's law is dead, what happens? 

To answer this question we need to look at the industry as it is, and actually analyze *how* the software industry is organized around improvements to hardware, and to what extent its economic strategy relies on the continuance of Moore's law. Then we can 'pull out the Jenga piece' and consider what would happen to the software industry if it no longer had Moore's law to back it up, and how the hardware industry would react. Then we can look at existing trends in the latter to see how they would resolve this contradiction.

Some evidence that Moore's law is at best transitory and at worst marketing gibberish: the existence of [[groschs-law]]

[[history-of-computing]]