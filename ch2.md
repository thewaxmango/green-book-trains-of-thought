# Chapter 2

## 2.1 Brain teasers

### Screwy Pirates

We can't understand how the most senior pirate will act without understanding the rest of the pirates, so we should start from the bottom of the hierarchy. We will denote coin splits from most senior to most junior, and votes as yea/nay. Let the most senior pirate be A, and the most junior be E. 

Suppose there is one pirate left. This is trivial, so we don't care about this case.

Suppose there are two pirates left, D and E. Then, the D proposes a 100/0 split, and the vote goes 1/1, meaning that the proposal is accepted. Therefore, E would accept any proposal when there are three pirates left, as long as they get nonzero coins.

Suppose there are three pirates left. Due to what happens at two pirates left, a 99/0/1 split is always accepted. Therefore, D should accept any proposal when there are four pirates left, as long as they get nonzero coins.

Suppose there are four pirates left. By the same logic, a 99/0/1/0 split is always accepted. C and E will accept any nonzero proposal from A when there are five pirates left, so the solution is **98/0/1/0/1**.

### Tiger and Sheep

We know that a tiger will only eat a sheep if they are guaranteed to not be eaten afterward. To understand if the case of 100 tigers and 1 sheep will result in a tiger eating a sheep, we must determine if at 99 tigers and 1 sheep, a tiger will still eat a sheep. We thus consider from the base case and work up.

At 1 tiger, the tiger will eat.

At 2 tigers, neither tiger will eat, as they will be eaten

At 3 tigers, a tiger can eat as then there would be 2 tigers left, and neither wants to eat or they will in turn be eaten.'

We extrapolate that on odd tigers, a tiger will eat the sheep, and vice versa on even tigers. Therefore, when there are 100 tigers, **the sheep will not be eaten**.

## 2.2 Logic reasoning

### River Crossing
To get to the other side with one torch, the torch must cross back and forth. Two people cross, then at least one must return. In total, there are 5 crossings (8 people total), as 2 across -> 1 back -> 2 across -> 1 back -> 2 across nets all four people successfully crossing the bridge. Furthermore, each individual must cross an odd number of times in total.

The simple immediate idea is to have A accompany every time, netting a cost of 10 + 1 + 5 + 1 + 2 = 19. We now want to find a better solution.

First, we know that the slower person bounds the time to cross. We can imagine the total cost as first the cumulative time of all people's crossings, regardless of overlap, then consider it overlap as saving the faster person's time. 

Optimally, we want D to cross 1 time, since D bounds every trip. Then, with the 7 total crossings left, we can distribute them 5/1/1 or 3/3/1 (order-agnostic). We know that C must cross once, as if this is not the case, the minimum cost we can naively (not considering possible) have is 

10 (D and C) + 5 (C) + 5 (C and A) + 1(A) + 2(B and A) = 23, which is greater the cost of 5/1/1/1 (A/B/B/C) before considering savings.

The other two cases are 5/1/1/1 and 3/3/1/1, the first of which we already explored and is not possible to overlap C and D. We try 3/3/1/1 with saving 5 on overlapping C and D, but we note that C+D can not be the first or third crossing as otherwise one of them must make a return trip. Thus, the first and last trip must be A+B, and due to parity, both of them must make exactly one return trip, totaling 2 (A and B) + 1 (A) + 10 (C and D) + 2 (B) + 2(A+B) = **17**.

### Birthday problem

We know from the reader POV's first statement that the month has at least one possible date, and that all the dates in that month are also ambiguous - otherwise they wouldn't be able to definitively say that C doesn't know. This reduces our options to March and September, which C is then able to derive the answer from. The reader then knows that the date can not be 5, as it would still be ambiguous to C. Finally, the reader is able to derive the answer, meaning that once 5s are ruled out, the date must be unique, so the answer is **Sep 1**.

### Card Game

Notice that the casino wins on ties, and the only way you win is if you have more. However, consider the only way cards are discarded - in pairs of black and red. Thus, ties are the only possible outcome, so the expected value is **$0**.

### Burning Ropes

Burning a rope from one end will not help us at all, since it takes an hour to burn through and we have no reference in the middle. If we burn both ends at the same time, we guaranteed measure half an hour - but that is not good enough. How can we measure 15 minutes?

First, we notice that the reason we can measure 30 minutes is because the rope is burning at 2 points, therefore consuming the rope at twice the speed. What if we ensure that a rope is constantly burning at 4 points? Suppose we light the rope at the center and the two ends (center is 2 points as the fire burns both ways). Then, when one pair of flames meet (killing 2 points), simply light the median of the unburnt segment that the other two flames are moving towards. Repeat until the rope is gone, measuring an additional 15 minutes.

Thus, in any order, perform the 30 minute burn and the 15 minute burn consecutively.

### Defective Ball

Let us consider this problem from a data standpoint. There are 24 cases: each of the 12 balls (A-L) being light or heavy. In order to determine the solution in 3 measurements, we have to rule out at least 22 of the cases.

Suppose we start by measuring A-D/E-H. We end up with two cases: balanced or unbalanced. Both cases result in 16 eliminated cases, or 2/3 of 24.

If balanced, we know that the outlier is in I-L. Then, measure I/J. If balanced, the outlier is in K/L, and I/J are normal. We can compare one of K/L with one of I/J. If balanced, the non-compared one of K/L is outlier and vice versa.

WLOG, suppose that A-D is heavier. Then, we know that the result is either one of A-D being heavier or one of E-H being lighter. We want to ensure that we can find the results in 2 comparisons, and we must eliminate 7 cases. 

What's the largest number of cases we can eliminate in the final comparison (given our extra balls that we know to be normal)? We could for example have A/B/E left, compare A/B, and know the answer (as we know A-D can only be heavy). This eliminates 2 cases. Then, we must eliminate at least 5 cases in the next comparison. This is less than 2/3 of 8, which gives us hope.

Suppose that WLOG we compare CFG/DHI. If balanced, we know the outlier is in A-heavy/B-heavy/E-light. If left is heavier, we know the outlier must be C-heavy or H-light, which is easy to identify. If the right is heavier, we know the outlier must be D-heavy/F-light/G-light, which we also previously know we can identify. For the sake of brevity, **the complete solution will be omitted**.

