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

At 3 tigers, a tiger can eat as then there would be 2 tigers left, and neither wants to eat or they will in turn be eaten.

We extrapolate that on odd tigers, a tiger will eat the sheep, and vice versa on even tigers. Therefore, when there are 100 tigers, **the sheep will not be eaten**.


