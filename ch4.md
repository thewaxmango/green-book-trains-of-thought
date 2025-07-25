## 4.1 Basic probability definitions and set operations

### Coin Toss Game

We notice that there is a symmetry - you always have one more flip than your opponent. If that flip is heads, you need to be tied or better with your opponent on the first *n* flips. If that flip is tails, you need to be have more than your opponent on the first *n* flips. By symmetry, the second part is equal to the probability you have less than your opponent, which when added together with the probability that you are tied or better is 1. Multiply by the probability of each outcome and get **0.5**.

### Card Game

You want to the know probability of getting a better card. We know the probability *b* of getting a better card is equal to the probability *w* of getting a worse card. Furthermore, let the probability of tying be *t*. Then, *1 = b + t + w -> b = (1 - t)/2*. 

Finding *t* is simple - the probability that you tie is the same as the probability that the top 2 cards are the same - which given any top card is 3/51 = 1/17 for the second card to also be the same. Then, *b* = **8/17**.

### Drunk passenger

First, we try and model a situation. Suppose the first person A chooses a random seat B. Then, no matter how many people between A and B come in, only A will be out of place in B, and seat A is empty. When B comes in, there is a 1/X (depending on how many people came in) that he sits in A's seat, otherwise there will still only technically be one out of place (when you hide the actual people and only consider what seats should have been filled). So when it comes your turn, either seat A is empty or your seat is empty. Furthermore, to all the other passengers, seat A and your seat are symmetric, including person A! Thus, the probability you get your seat is **1/2**.

### N Points on a Circle

Suppose WLOG that the point on the clockwise side of the largest gap is point 1. Then, to all fit on a semicircle, all other N-1 points must be on the next semicircle clockwise from point 1, which has probability over all N possible gap-clockwise points  **0.5^N-1^N**. 

## 4.2 Combinatorial analysis

### Poker Hands

We count how many combinations of hands that fit the criteria someone may get and divide by the total number of combinations of hands. Note: this is the same as permutations as all cards are considered to be distinct.

Total combinations: 52C5 = 52!/(5!47!). For all following criteria, the probability is the number of combinations found divided by 52C5. We leave products unsimplified as the actual result is not necessary for understanding the problem as long as the value is correct.

4 of a kind: we choose one suit for the 4 of a kind, and one extra card -> 13C1 \* 48C1 = **13\*48**. 

Full house: we choose one suit for the 3, one suit for the 2, and the specific cards in each suit -> 13C1 \* 12C1 \* 4C3 \* 4C2 = **13 \* 12 \* 4 \* 6**.

Two pair: we choose two suits for pairs, one extra card, and the specific cards in each suit -> 13C2 \* 44C1 \* 4C2 \* 4C2 = **(13 \* 6) \* 44 \* 6 \* 6**.

### Hopping Rabbit

To determine the number of ways the rabbit gets to the *n* th step, it is the sum of ways to get to the *(n-1)* th step and the ways to get to the *(n-2)* th step. We know the number of ways to get to the zeroth step is 1, and the first step is 1. F(2) = 2, F(3) = F(1) + F(2) = 3... This is the Fibonacci sequence, and for the *n* th step, you take the ***n+1* th Fibonacci number**.


