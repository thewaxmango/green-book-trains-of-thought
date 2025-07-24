## 4.1 ~~~~~

### Coin Toss Game

We notice that there is a symmetry - you always have one more flip than your opponent. If that flip is heads, you need to be tied or better with your opponent on the first *n* flips. If that flip is tails, you need to be have more than your opponent on the first *n* flips. By symmetry, the second part is equal to the probability you have less than your opponent, which when added together with the probability that you are tied or better is 1. Multiply by the probability of each outcome and get **0.5**.

### Card Game

You want to the know probability of getting a better card. We know the probability *b* of getting a better card is equal to the probability *w* of getting a worse card. Furthermore, let the probability of tying be *t*. Then, *1 = b + t + w -> b = (1 - t)/2*. 

Finding *t* is simple - the probability that you tie is the same as the probability that the top 2 cards are the same - which given any top card is 3/51 = 1/17 for the second card to also be the same. Then, *b* = **8/17**.
