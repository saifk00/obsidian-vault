#cryptography 
Suppose three parties A, B, and C want to determine who makes the most money but without sharing their exact salaries with eachother. If they had a trusted fourth party D, D could take their salaries and compute $F(s_A, s_B, s_C) = \text{max}(s_A, s_B, s_C)$. 

The **millionaire's problem** is to compute this function *without* needing this fourth party.