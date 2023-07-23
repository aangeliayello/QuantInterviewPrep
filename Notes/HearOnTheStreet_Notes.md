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

Number of hands with of 4 of a kind:
(Ways to choose the number of the 4 of a kind) * (Ways to chose that 4 of a kind) = 13 * 48 

Number of hands with a Full house
(Ways to choose the tripe) * (wats to choose the the suits of the triple) * (ways to choose the pair) * (ways to choose the suits of the pair) 
13 * (4 choose 3) * 12 * (4 choose 2)

Number of hands with two pairs: 
We can use the same approach as above with one consideration. Since the trip and the pair are different the approach works because triple of K and pair of Q is not the same as a trip of Q and a pair of K. In this case we would be double countin the pairs, since a pair of K and Q is the same as a pair of Q and K. Thus, we have

13 * 12 / 2 * (4 choose 2) * (4 choose 2) 

This is equivalent to 

(13 choose 2) * (4 choose 2) * (4 choose 2)

#### Hopping Rabits

Say we want to calcute the different ways to go up the stair with n steps but we already calculated it for 1, 2, ..., n-1 then the first move can either be a 2-hop or a 1-hop. If it is a 1-hop the remaining ways from there is the same as the n-1 steps stair and if we do a 2-hop the remaining ways from there is the same as the n-2 steps stair, thus, we have a fibonaci sequence patter where 
$$f_n = f_{n-1} + f_{n-2}$$

### Screwy Pirates 2

https://math.stackexchange.com/questions/581461/what-is-the-minimum-number-of-locks-on-the-cabinet-that-would-satisfy-these-cond

### Chess Tournament
This one is easy if we use the right approache, since it is a knockout tournatment there are two branches of the tree, and if 1 and 2 are in different branches then they will meet in the final. Thus, the probability of 2 being in the different branch to of 1 is 
$$\frac{2^{n-1}}{2^{n} - 1}$$
So, just lightly aboth 1/2 for big values of $n$. 

