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

### River Crossing
To get to the other side with one torch, the torch must cross back and forth. Two people cross, then at least one must return. In total, there are 5 crossings (8 people total), as 2 across -> 1 back -> 2 across -> 1 back -> 2 across nets all four people successfully crossing the bridge. Furthermore, each individual must cross an odd number of times in total.

The simple immediate idea is to have A accompany every time, netting a cost of 10 + 1 + 5 + 1 + 2 = 19. We now want to find a better solution.

First, we know that the slower person bounds the time to cross. We can imagine the total cost as first the cumulative time of all people's crossings, regardless of overlap, then consider it overlap as saving the faster person's time. 

Optimally, we want D to cross 1 time, since D bounds every trip. Then, with the 7 total crossings left, we can distribute them 5/1/1 or 3/3/1 (order-agnostic). We know that C must cross once, as if this is not the case, the minimum cost we can naively (not considering possible) have is 

10 (D and C) + 5 (C) + 5 (C and A) + 1(A) + 2(B and A) = 23, which is greater the cost of 5/1/1/1 (A/B/B/C) before considering savings.

The other two cases are 5/1/1/1 and 3/3/1/1, the first of which we already explored and is not possible to overlap C and D. We try 3/3/1/1 with saving 5 on overlapping C and D, but we note that C+D can not be the first or third crossing as otherwise one of them must make a return trip. Thus, the first and last trip must be A+B, and due to parity, both of them must make exactly one return trip, totaling 2 (A and B) + 1 (A) + 10 (C and D) + 2 (B) + 2(A+B) = **17**.
