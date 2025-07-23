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

### Birthday Problem

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

### Trailing Zeros

Very easy. Consider the prime factorization of 100! = 2^a \* 3^b \* 5^c... We know that the number of trailing zeroes is min(a, c). Furthermore, we know that a > c for any factorial above 1!, as there are at least two multiples of 2 for every multiple of 5, and higher powers are even more biased. Thus, we identify how many powers of 5 there are in 100! -> this is 100 // 5 + 100 // 25 + 100 // 125... = 20 + 4 + 0... = **24**.

### Horse Race

We want to figure out at way to eliminate 22 of the 25 horses. Naively, we can eliminate at least 2 horses in every race, bringing our upper bound down to 11. We also can't decide on what the fastest horses are without comparing all horses at least once, bringing our lower bound to 6 (as comparing exactly once means no cross-comparing). Consider the best case scenario where we know A>B>C>D>E, F>G>H>I>J, etc. Then, we learn C>F>K>P>U, giving us the information we need. However, this is in fact the only way to determine the best in 6, and relies on us getting lucky where we get the three fastest A>B>C... and hit the 1/4 of comparing C with all the other race winners.

What are our ways to guarantee elimination of more per race? Suppose we know A>F, B>G, C>H, D>I, and E>J. Then, when we learn A>B>C>D>E, we know that D, E, H, I, and J are eliminated. How about we expand on this idea?

Let us consider A>B>C>D>E, F>G>H>I>J, etc. again, but this time choose to compare all the race winners. Then, we learn WLOG A>F>K>P>U, meaning that our candidates are reduced to A, B, C, F, G, and K. Furthermore, we know A is the fastest. Finally, we race B, C, F, G and K to find the next 2, taking 7 races. 

### Infinite Sequence

We want to solve the classic x^(x...)^ = 2 problem. Then, log_x(x^(x...)^) = log_x(2) ->  x^(x...)^ = log_x(2) -> 2 = log_x(2) -> x^2 = 2. The solutions to this are x = +-sqrt(2), but the negative solution can not be a log base, so **x = sqrt(2)**.

## 2.3 Thinking out of the box

### Box Packing

Let us consider 2x2x2 checkerboard parity. Each 1x1x4 occupies two minoes of each parity, meaning the total occupancy of all 53 blocks is 106 of each parity. However, in a 6x6x6, there are 14*8=112 of one parity and 13*8=104 of the other, meaning this packing is not possible.

### Calendar Cubes

We know that 0, 1, and 2 must be on a different cube from an occurrence of all other digits (except 0-0). These numbers must occur on both dice. 30 and 31 are covered by 03 and 01. Then, there are only 6 slots left for 7 digits, meaning the problem pulls some BS like flipping the 6 for a 9. Then, distribute 3-8 between the 2 dice arbitrarily.

### Door to Offer

Notation wise, let answer cases be determined by the guard and door we are at: <truth, job offer>/<truth, exit>/<lie, offer>/<lie,exit>. Simple questions include "Is this the job offer?" (T/F/F/T) or "Are you the liar?" (F/F/F/F).

We need to identify out of four cases - which door we are at as well as which one of the two guards we are talking to. Since we only get one bit of information from the question, we must direct this question in order to determine which door we are at, which is a truth table of T/F/T/F, where T is stay and F is switch.

So how do we fix the lying guard problem? What if we try some sort of error correction by combining the answers to the two questions? We can ask a position agnostic question like **"Is the truth telling guard in front of the job offer?"**, giving us T/F/T/F, which is exactly what we want.

### Message Delivery

Obviously, we can not send a message to a person with a locked box if they do not own the lock. Thus, we need to somehow obtain the other person's lock without losing it. So, how do we get their lock on the box with our message inside? They can not send their padlock to us unlocked, or their lock locked without the message inside. 

Let us formulate this as a sequence of actions for persons A and B: A inserts message, A locks, A unlocks, Pass box, B locks, B unlocks, B receives message. A inserts message must occur first, as no locks can be on. Then, A locks, as Pass box will just lose the message. Then, all A can do is Pass box. B can not unlock or receive message. Passing Box again is useless, so B locks and Pass box is the only logical solution. This is followed by A unlock, Pass box, B unlock, and B receives message. Sequence: **insert message, A locks, send box to B, B locks, send box to A, A unlocks, send box to B, B unlocks, receive message**.

### Last Ball

Yet another parity problem. We usually identify this sort of problem by the binary (or n-ary) nature and state changes. Let blue be 0, red be 1, and the invariant be the sum of the balls mod 2. Note that this invariant exists because removing two equal balls (sum 0 or 2) and adding a blue (0) maintains the invariant. Removing two different balls (sum 1) and adding a red (1) maintains the invariant. **With 20 blue and 14 red, last ball will be blue** as the parity is 0. **With 20 blue and 13 red, last ball will be red**.

### Light Switches

Naively, just try each one in turn and take 4 turns. What if we flip multiple? Flipping 2 rules out half the options, and flipping one of the 2 remaining possibilities rules out another. Thus, **2 turns**.

*On review*: it turns out that the answer involves touching the lightbulb and gaining two bits of information on one entry to the room. Should have seen it coming...

### Quant salary

We want to figure out a way for everyone to add up their salaries without knowing any other person's salary. There are two possible ways to do this: first is that a person only reveals partial information about their salary, second is that a person reveals some encrypted version of their salary. I can not think of a good way to do this without some trusted third party.

Criticisms of the given answer: If two quants (e.g. 3 and 5) share their numbers, they can determine what 4's salary is.

## 2.4 Application of symmetry

### Coin Piles

Let's consider what happens when we choose to flip some coins. Suppose there are *h* heads of 1000 coins, and we flip some *m* of them. Suppose there are *i <= m* heads in those. Then, the resulting number of heads is *h-i+(m-i) = h+m-2i*, with *h-i* in pile 1 and *m-i* in pile 2. How do we make them equal? Well, easy. Set *h=m*, or in English, **arbitrarily separate out 20 coins and flip them**.

### Mislabeled Bags

Note that all bags are mislabeled. What do we know from that? Well, the bag labeled as the mixed bag must either be apples or oranges. Retrieve one fruit to confirm which, WLOG say it is apples. Then, the other two bags are labeled apples and oranges. We know the bag labeled oranges is not oranges and it is not apples (as that is the bag labeled mixed). Then, that bag must be the mixed bag, and one labeled apples is oranges.

### Wise Men

We need some way to ensure that everyone has visited the room, but we can not encode the number of distinct visitors in the one bit of information. However, we can encode whether a distinct person has visited - so what if we have one wise man use their brain as a counter, and everyone only flips upside down if it's their first time getting a chance to flip the cup from right side up to upside down? Then, when the counter visits, he sees if a new person has visited the room, and flips right side up. Once 49 flips have been counted, the counter declares that everyone has visited the room.

## Series summation

### Clock Pieces

Three pieces, equal sums. We know the numbers on the clock sum to 12*13/2 = 78. Then, each part must sum to 26. We also know that at least two pieces must contain contiguous numbers, as it is impossible to break a clock into only 3 pieces otherwise. Consecutive sums to 26: **11-12-1-2, 5-6-7-8**. Last piece is **9-10-3-4**.

### Missing Integers

There is no way to solve this in better than *O(n)* time, so I will assume the solution wants *O(1)* additional space. Let the missing numbers be *a, b*. Since we are operating in constant space, we must accumulate the numbers somehow. A system of two equations allows us to identify two variables from two results. 

Let us take the sum of all the numbers = *5050-a-b*. This allows us to determine *c=a+b*. Let us take the product and identify *p=ab*. Then, *c^2^-4p=(a-b)^2^=K^2*, which gives us *K=a-b* or *K=b-a*. Solving gives us two pairs which are identical, but reversed - this is the solution

## Series summation

### Clock Pieces

Three pieces, equal sums. We know the numbers on the clock sum to 12*13/2 = 78. Then, each part must sum to 26. We also know that at least two pieces must contain contiguous numbers, as it is impossible to break a clock into only 3 pieces otherwise. Consecutive sums to 26: **11-12-1-2, 5-6-7-8**. Last piece is **9-10-3-4**.

### Missing Integers

There is no way to solve this in better than *O(n)* time, so I will assume the solution wants *O(1)* additional space. Let the missing numbers be *a, b*. Since we are operating in constant space, we must accumulate the numbers somehow. A system of two equations allows us to identify two variables from two results. 

Let us take the sum of all the numbers = *5050-a-b*. This allows us to determine *c=a+b*. Let us take the product and identify *p=ab*. Then, *c^2^-4p=(a-b)^2^=K^2*, which gives us *K=a-b* or *K=b-a*. Solving gives us two pairs which are identical, but reversed - this is the solution.

### Counterfeit Coins

We must determine a way to weigh only once and differentiate every bag. This is only possible if we add a different number of coins from each bag, as if we add X coins from two different bags, the weighing result can not differentiate. Then, if we add 1 coin from one bag, etc. we can only differentiate the 1-coin bag and the 3-coin bag as the outlier if there is no mixing of 9s and 11s in the outlier bag, but once we are there we find the absolute difference of (1 + 2... 10)*10 = 550 from the weight, which indicates the bag.

### Glass Balls

We only have two balls, and want to find the floor. Suppose the first toss is at floor M_0, and it breaks. Then, we must start throwing from 1 upwards to M_0 to ensure we don't break before the solution is found, which has a worst case of M_0 throws.

Suppose the first throw doesn't break. Then, we choose some M_1>M_0 to try, and if it breaks, takes M_1-M_0+1 throws. In order to minimize worst case throws, let M_1-M_0+1=M_0 -> M_1 = 2M_0-1. If doesn't break, continue with M_2=3M_0-2-1... We want to ensure that M_(M_0)- M(M_0-1) + M_0 = M_0 and that M_(M_0) >= 100, implying that M_(M_0) = M(M_0-1) (which is true by examining the summations). We know M_(M_0) = (M_0 + 1)M_0 - (1 + 2 + ... + M_0) = (M_0 + 1)M_0/2, for which the minimum solution is M_0=14.

## 2.6 The Pigeon Hole Principle

### Matching Socks

This is super basic - worst case you grab one of each color, then on the **4**th, you get a pair with one of the first three.

### Handshakes

Everyone could have shaken hands with 0-25 people. However, 25 and 0 are mutually exclusive (and 0 is not possible, since you shake hands with everyone), so the space is reduced to 25 choices, which for 26 people **must indicate sharing of at least one number**.


### Have We Met Before?

This indicates that in a graph containing six nodes, there must be a subset of three nodes that is complete or empty. We can prove that this is true by attempting to construct a graph with neither, and show that it is impossible. We may try smaller cases first just to indicate get a sense of how it works.

First, we prove that the only way to construct a graph with 5 nodes that doesn't have either a complete or empty triplet is a ring. Let us first consider the number of edges necessary. 

Suppose there exist <=4 edges. Then, either at least one node is disconnected or the graph is a tree. If one node is disconnected, by the pigeonhole principle we may select another pair of nodes that do not share an edge and form an empty triangle. If the graph is a tree, then there must exist either three leaves (which can not share edges, or else the tree would have size 2) from which we can draw an empty triangle, or is a line, in which case we select the ends and the middle to form an empty triangle. 

Suppose there exist >=6 edges. Then, by pigeonhole principle, there must exist some node with at least three outgoing edges. Furthermore, by pigeonhole principle, at least 2 of those neighbors must share an edge, forming a complete triangle.

Then, 5 edges is the only case. It must be connected, as a lone node can form an empty triangle by pigeonhole principle (5/6 to connect 4 nodes). It can not have a loop of 3 (trivial) or a loop of 4 (the extra node can form an empty triangle with the diagonal of a square it is not adjacent to a node of). Thus, the graph of 5 nodes must be a ring. 

When we add the 6th node, it must connect to at least 3 nodes - otherwise, there exists a diagonal of the ring such that with the 6th node, it forms a empty triangle. However, with three edges, by pigeonhole it once again must form a complete triangle. Thus, this is impossible, so a graph with 6 nodes must contain either an empty triangle or a complete one.
