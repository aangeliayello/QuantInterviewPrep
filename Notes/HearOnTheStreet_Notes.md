# Heard On The Stree Notes and Answers

## Some chapters

## Probability Theory

### Basic Probability

#### Coin toss game
*Answer:* First, reduce the game to the case where both playes have the same number of tosses and let the probabilities of a P1 with be p1, P2 wins p2 (p1 = p2), and probability of a tie p3.

Then, the probility of a P1 win on the unbalanced games is 
$$ p1 + 0.5*p3 => p1 + 0.5*(1-2*p1) => 0.5$$

#### Card game
*Answer:* Similarly let the probability of a P1 win, P2 win, and tie be p1, p2, and p3, respectively. Then, the answer is 
$$p1 = (1-p2)/2 => (1-3/51)/2 = 8/17$$

#### Drunk Passenger
*Answer:* By induction it follows, saw N := 2, the it is clear that the probability of success is 1/2. Then, let probability of success for a plane with N seats is $P_N$ then 
    $$ P_{N+1} = 1/n + (n-2)/n * (1/2)  = 1/2$$
This follows from the fact that if the drunk passenger seat on his seat (1/n) then it is a success, if it seats on your seat (1/n) is a guaranteed failure but if it seats in any other seat ( (n-2)/n ) plane with m seats where m <= n, thus, by induction the probabity of success in the reduced game is 1/2, and the formula follows.

#### N points on a circle
In general, the probability of the union of mutually exclusive events is just the sum of the individual probabilities. 

Now, lets label the points in order p1, p2, ..., pn, then let Ei be the event of the points falling in a semicircle starting from the point pi and doing the semicircle clockwise. Now since the fraction of the circle is 1/2 (leq 1/2) we can see that if all the points fall in the cicle starting from pi then none of the other semicircles can have all the points as well. 

For simplicity say the semicircle starting from p1 contantains all the points. Then, the clockwise distance from from p1 to pi for any i is $\pi$ radians or less, then it follows that the clockwise distance from pi to p1, dist(pi, p1) = $2\pi$ - dist(p1, pi) > $2\pi - \pi = \pi$

### Combinatorial Analysis

#### Poker Hands

**Probability of 4 of a kind:**
