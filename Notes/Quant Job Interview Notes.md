# Quant Job Interview Notes
*Let $\epsilon$ approach $\infty$*


## Intro

## Option Pricing
PH

## Probability

### Question 3.1. Consider the following game. The player tosses a die once only. The payoff is 1 dollar for each dot on the upturned face. Assuming a fair die, at what level should you set the ticket price of this game?

Here, we just take the expected value of the payoff. 

$$E(D) = \frac{1}{6} ( 1 + 2 + ... + 6) = 3.5$$

#### Evaluate the expectation for an n—sided die, with n a positive integer.
It would follow a uniform discrete distributio with boundaries $1$ and $n$. Thus, the expected value is $\frac{n+1}{2}$

#### What is the expectation of the sum of two rolls?
If we assume they are independent the $E(D_1) + E(D_2) \equiv 2*E(D) = 7$

#### What is the probability of getting seven with two rolls?
Lets vizualize the rolls of the two dices on a 2d matrix with labes 1-6 as rows and colums denoting the row of the first and second die respectively. Then, we can see that the sum of the indices is equial to 7 in the anti-diagonal. Thus, out of the 36 possible outcomes 6 add up to 7. Therefor the probability is 1/6.


|       | **1** | **2** | **3** | **4** | **5** | **6** |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| **1** | 2     | 3     | 4     | 5     | 6     | 7     |
| **2** | 3     | 4     | 5     | 6     | 7     | 8     |
| **3** | 4     | 5     | 6     | 7     | 8     | 9     |
| **4** | 5     | 6     | 7     | 8     | 9     | 10    |
| **5** | 6     | 7     | 8     | 9     | 10    | 11    |
| **6** | 7     | 8     | 9     | 10    | 11    | 12    |


### Question 3.2. Suppose we play a game. I roll a die up to three times. Each time I roll, you can either take the number showing as dollars, or roll again. What is your expected winnings?

In this question we need to first decide on a strategy, and then calculate the expected value on the strate. 

**Strategy:** 
Lets base our strategy on the expected value of the payoff and disregard variance and any other aspect. Thus, in our strategy we will reroll of the expected value of the reroll is higher than the rolled outcome.

**Expected Value of the Payoff:**
To calculate the expected value of the payoff we need to work backwards.

We already know the expected value of the possible 3rd roll from the last question, 3.5. Thus, on the second roll we will roll if we get a 1, 2, or 3, else we stay. 

$$E(R_1) = 3.5$$

$$E(R_2) = \frac{3}{6}\left(3.5\right) + \frac{3}{6}\left(\frac{1}{3} ( 4 + 5 + 6)\right)= 4\frac{1}{4}$$

Similary for $R_3$ we reroll if we get anything under 4.75, and keep if we roll more, 5 or 6.

$$E(R_3) = \frac{4}{6}\left(4.25\right) + \frac{2}{6}\left(\frac{1}{2} (5 + 6)\right)= 4\frac{2}{3}$$

#### How many rolls would I need to offer you before you will only accept a 6 on the first roll?
If we continue the strategy the it we would accept a 6 on the first roll if the expected value of $R_{n-1}>5$. 

$$E(R_4) = \frac{4}{6}\left(4\frac{2}{3}\right) + \frac{11}{6}= 4\frac{17}{18}$$

We can conviencisly guess that $E(R_5) > 5$, so if we have a payoff with 6 allowed rolls (or 5 rerolls) then on the first roll we would only accept a 6. 

#### What sort of option does this problem relate to?
This recembles an american option, with we can exercise it at any time but we have the option to hold and wait. 

#### How does your answer change if the payment is the square of the number showing?
The same algorithms applies. If the current roll is greater than the expected payoff of a reroll, we stay. Now the values are squared so to recalculate the values of $R_1'$, $R_2'$ and so on.

$$E(R_1) = \frac{1}{6} \left(1 + 4 + 9 + 16 + 25 + 36 \right) = 15\frac{1}{6}$$

Since, a 4 gives of a payoff of 16 then we would reroll for 1, 2, and 3.

$$E(R_2) = \frac{3}{6}\left(15\frac{1}{6}\right) + \frac{3}{6}\left(\frac{1}{3} ( 16 + 25 + 36)\right)= 20\frac{5}{12}$$

Similary for $R_3$ we reroll if we get anything with payoff under 20\frac{5}{12}, and keep if we roll more, 5 or 6.

$$E(R_3) = \frac{4}{6}\left(20\frac{5}{12}\right) + \frac{2}{6}\left(\frac{1}{2} (25 + 36)\right)= 23\frac{7}{9}$$

#### What effect will it have if I charge you $1 for each additional roll?
Again, same logic applies but now the value of a reroll is $E(R_i) - 1$, and we will reroll if the payoff is less than  $E(R_i) - 1$.

$$E(R_i) = \alpha \left[ E(R_{i-1}) - 1\right] + (1-\alpha)\left( \dots \right)$$

### Question 3.3. Let's play a game. There are four sealed boxes. There is 100 pounds in one box and the others are empty. A player can pay X to open a box and take the contents as many times as they like. Assuming this is a fair game, what is the value of X?

The first intuitive question that comes to mind whether or not I am willing to pay more than 25 (100 / 4) per try? Then answer is yes. Clearly, we are willing to pay 25, but also 25 + $\epsilon$ since it is unlikely that it takes us 4 tries and we would make enough if we get the price with 1, 2, or 3 tries. 

In essense we want to find an $X$ such that the expected cost is equal to the expected payoff, namely 100. (This is assuming we will play untill we find the price, which intuitively it makes sense since the cost is constant and the game becomes more attractive as there are less boxes.)

Now, lets calculate the expected cost. Let $R$ denot the number of rolls, then $E(Cost) = X E(R)$
$$P(one\ play) = \frac{1}{4}$$
$$P(two\ play) = \frac{3}{4} \frac{1}{3} = \frac{1}{4}$$
$$P(three\ play) = P(four\ play) = \frac{1}{4}$$

Then, we have that 

$$E(R) = \frac{1}{4}\left(1 + 2 + 3 + 4\right) = 2\frac{1}{2}$$

$$X \leftarrow  100 / 2.5 = 40$$

#### Instead of maintaining a constant price, if you choose to continue playing after two incorrect guesses the price changes to Z. What is the fair value of X and Z?
Here again, we have to solve the problem backwards. First, we find Z as we found $X$ above, and then we can continue to find $X$. 

TODO: Finish calculations
#### Generalise the above problem to the case of n boxes.
TODO

### Question 3.4. We play a game: I pick a number $n$ from 1 to 100. If you guess correctly, I pay you $n$ and zero otherwise. How much would you pay to play this game?

First, we need to assume that the strategies are known to both players. Then, it follows that no deternimistic strategy from the host will be successfull since it can be always countered.

Now, we have that the choosing strategy needs to be random. Then the strategy will have the following form 
$$P(b_i) = p_i\ where \sum p_i = 1$$

Then, we need to decide how to distribute the probabilities. If we assume we only have two boxes with values $a$ and $b$. Then, we conjecture that the best strategy is 
$$p_a = \frac{1/a}{d};\ \ p_b = \frac{1/b}{d};\ \ d = 1/a+1/b$$

Then, the payoff for the player if it always plays $a$ or always plays $b$ is on average $1/d$. Thus, any other mix of trategies will also pay $1/d$.

Now assume we use $p_a'$ and $p_b'$ where $p_a' < p_a$, and respectively $p_b' > p_b$. Then, the strategy of playing only $b$ would pay more tha $1/d$. We can see (handwavevly) that any other distribution of probabilities would be better for the player, thus, since it is ta zero-sum game the host will go for the initial probability distribution of $p_i \propto 1/i$.

Then, if with assume this strategy it follows that the payoff is 
$$\frac{1}{D}\ where\ D = \sum^{100}_{i=1}1/i$$

#### What if you receive the number squared?
Note that the arguments where agnostic of the actual value of the boxes, thus, the same reasoning follows and we have a payoff of 
$$\frac{1}{D'}\ where\ D' = \sum^{100}_{i=1}1/i^2$$

#### Why should the value decrease as the number of numbers increases?

In general we have the form of the payoff for $n$ boxes as follow

$$\frac{1}{D^*}\ where\ D^* = \sum^{n}_{i=1}1/i^2$$

And, sind $D^*$ is increasing in $n$ it follows that the payoff is decreasing in $n$. 

Note that for the case of non-squared payoff the value of the game will aproach zero since the sum of the harmonic series will diverge. But for the square case it will converge!

### Question 3.5. Suppose you have a fair coin. You start with a dollar, and if you toss a H, your position doubles, if you toss a T, your position halves. What is the expected value of the money you have if you toss the coin infinitely?

Given that the tosses are independent the question reduces to findig the expected value of the first toss since. 

$$E(X_1 \cdot X_2 \cdot \dots \cdot X_n) = \prod E(X_i)$$
for independent $X_i$. Since $E(X_1) = 5/4$, it follows that 

$$E\left(\prod X_i\right) = (5/4)^n$$

#### Suppose your position increases by a factor of x on a $H$ instead of 2. Classify the long term behaviour as a function of x.

The general form is
$$E(X_1) = \frac{1}{2} \left( 1/x + x\right)= \frac{x^2 + 1}{2x}$$

$$E\left(\prod X_i\right) = \left(\frac{x^2 + 1}{2x}\right)^n$$

Then, the behavior of the expectactions depends on the relationship between $x^2 + 1$ and $2x$. 

When we solve the equation 

$$x^2 - 2x + 1 = (x - 1)^2=0$$

we have that the only zero is at 1. And $x^2 + 1$ is never less than $2x$ (this also follows from the inverse symentry of x and 1/x).

So the long term behavior is divergence to infinity for $x > 1$, and static at 1 for $x = 1$

#### Suppose your position increases by a factor of x on a H and is multiplied by y with y < 1 otherwise. Classify the long term behaviour as a function of x and y.

$$E(X_1) = \frac{x+y}{2}$$

$$E\left(\prod X_i\right) = \left(\frac{x+y}{2}\right)^n$$

Thus, it follows that 

$$E\left(\prod X_i\right) = \left(\frac{x+y}{2}\right)^n$$

$$
    E\left(\prod X_i\right) = 
    \begin{cases}
        0, & \text{for } x+y<2\\
        1, & \text{for } x+y=2\\
        \infty, & \text{for } x+y>2 
    \end{cases}
$$


### 3.6. Suppose we toss a fair coin, and let N denote the number of tosses until we get a head (including the final toss). What is $E(N)$ and $Var(N)$?

This is a geometric random variable, but lets derive the figures from scratch. Let $p$ be the probability of the coin landing heads. 

$$P(N=0) = 0$$
$$P(N=1) = p$$
$$P(N=2) = p(1-p)$$
$$P(N=n) = p(1-p)^{n-1} for\ n\geq1$$

$$E(N) = \sum_{n=0}np(1-p)^{n-1}$$
$$E(N) = p \frac{d}{dp}\left(-\sum_{n=0}(1-p)^{n}\right)$$
$$E(N) = p \frac{d}{dp}\left(-\sum_{n=0}(1-p)^{n}\right) = p /p^2 = 1/p$$

Deriving this I am realizing that I am not fully convienced by the integral/derivative argument. 

Let's use a cleaner argument

$$E(X) = pE(X| X_1 = H) + (1-p)E(X|X_1 = T) $$
$$= p\cdot1 + (1-p)(E(X) +1) = 1/p$$

Similarly 

$$E(X^2) = pE(X^2| X_1 = H) + (1-p)E(X^2|X_1 = T) $$
$$= p\cdot1 + (1-p)\Bigl(E(X^2) + 2E(X)+1\Bigr) = \frac{1-p}{p^2}$$

So, now we just plug $p:= 1/2$ to get $E(X) = 2$ and $Var(X) = 2$.

#### I pay you $1 at the end of this year, $2 at the end of next year and so on. The effective annual interest rate is i. Derive, from first principles, the value of this payment stream.

TODO

#### Derive the expectation and variance of a random variable with a Poisson distribution.

TODO

#### What is the mean and expectation if we redefine N to be the number of tails before we toss a head?

We note that the random variable $Y$ follow $Y\simX-1$. Thus, $Var(Y)$ is the same, and $E(Y) = \frac{1-p}{p}$.

### Question 3.7. We play a game, with a fair coin. The game stops when either two heads (H) or tails (T) appear consecutively. What is the expected time until the game stops?

This should be solvabable by breaking down the expected value into conditional events.

Let $P(H) = p$ and $P(T) = q = (1-p)$

$$E(X) = pE(X|[TH]) + qE(X|[HT])$$

$$E(X|[TH]) = pE(X|[HH]) + qE(X|[HT])$$

$$E(X) = p[p + qE(X|[HT])] + qE(X|[HT])$$


$$\begin{aligned} 
E\left(X\right) & =p^2(E(X|HH)+1) \\ 
& + p^2(E(X|HH)+2) \\ 
& + q^2(E(X|TT)+2) \\
& + pq(E(X|HT)+2) \\
& + pq(E(X|TH)+2) \\
\end{aligned}$$

$$\begin{aligned} 
E\left(X|HT\right) & =p(1+ E(X|TH)) + q & = pE(X|TH) + 1\\ 
E\left(X|TH\right) & =p + q(1+ E(X|HT)) & = qE(X|HT)  + 1\\ 
\end{aligned}$$
 
and from the above pair of equations it follows that 
$$\begin{aligned} 
E\left(X|HT\right) & =\frac{1+p}{1-pq} \\ 
E\left(X|TH\right) & =\frac{1+p}{1-pq}  \\ 
\end{aligned}$$


$$E(X) = 2p^2 + 2q^2 + pq(4 + \frac{3}{1-pq})$$

and if we plug $p=q=1/2$ we get $E(X)=3$.


#### What is the variance of N?
TODO:\
I did the derivation in the sumation form an it gets pretty nasty, wondering if there is a cleaner approach.

#### How is the expectation changed if we alter the game so we need three consecutive occurrences of either heads or tails to end the game?
TODO

### Question 3.8. For a fair coin, what is the expected number of tosses to get three heads in a row?
TODO

### Question 3.9. You toss a biased coin. What is the expected length of time until a head is tossed? For two consecutive heads?

See Question 3.7, it should be a straight fwd addaptation.

### Question 3.10. I have a bag containing nine ordinary coins and one double-headed one. I remove a coin and flip it three times. It comes up heads each time. What is the probability that it is the double-header?

We are asked to caculte the following conditional probability. Let $dp$ and $rc$ denote the events of grabing a double-side or a regular coin respectively.

$$\begin{aligned} 
P(dh | HHH) &= \frac{P(dh \cap HHH)}{ P(HHH) }\\ 
&= \frac{P(dh)}{\left( P(dh) + 1/8 P(rc) \right)  }  \\ 
\end{aligned}$$

Thus, for this set up we get
$$\begin{aligned} 
P(dh | HHH) &= \frac{1/10}{\left( 1/10 + 1/8\cdot 9/10 \right)  } = \frac{8}{17} \\ 
\end{aligned}$$


#### What if there are two double-headed coins?
For this we use the expresion above but use $dh \rightarrow 2/10$ and $rc \rightarrow 8/10$.

$$\begin{aligned} 
P(dh | HHH) &= \frac{2/10}{\left( 2/10 + 1/8\cdot 8/10 \right)  } = \frac{16}{24} \\ 
\end{aligned}$$

We note that the denominator gained 7 and the denominator gained 8. It is the case for the next step as well? With out calculating it makes sense after 10 rounds (8 more) the numberator would catch up with the denominator and have $$P(dh | HHH)  = 1$$ (since all conins are double-headed).

Turns out it is the case indeed. Let $n$ be the number of double-headed coins then the generic form is 

$$\begin{aligned} 
P(dh | HHH) &= \frac{8n}{10+7n}
\end{aligned}$$

#### How many tosses would you need to be 95% sure that the coin is double-headed?

**INTERESTING_QUESTION**

Instictively, I am woundering if I can massage the problem and use some normallity distribution properties.

Let's formalize the problem first. Let $H_k$ denote the event of $n$ heads flipped in a row. Then, the question is what is the smallest $n$ such that 

$$P(dh | H_k) > 0.95$$

Now that the problem is formallized it doesn't look as intimidating... Thus, lets tacket the generalization; let $p$ the probability of heads, $n$ the number of double-headed coins and $m$ the number of regular coin. 

$$
\begin{aligned}
P(dh | H_k) &= \frac{\frac{n}{n+m}}{\frac{n}{n+m} + p^{k}\frac{m}{n+m}}\\
&= \frac{p^{-k}{n}}{p^{-k}{n}+ {m}}
\end{aligned}
$$


$$
\begin{aligned}
P(dh | H_k) &= \frac{2^{k}}{2^{k}+ {9}}
\end{aligned}
$$


$$
\begin{aligned}
\frac{2^{k}}{2^{k}+ {9}} = \alpha\\
2^{k}(1-\alpha) = 9\alpha  \\
k = log_2\left(\frac{9\alpha}{1-\alpha} \right)
\end{aligned}
$$


$$
\begin{aligned}
\frac{2^{k}}{2^{k}+ {9}} = \alpha\\
2^{k}(1-\alpha) = 9\alpha  \\
k \approx log_2\left(9*20 \right) \in (7, 8)
\end{aligned}
$$

Thus, we would need 8 throws


### Question 3.11. I take an ordinary-looking coin out of my pocket and flip itthree times. Each time it is a head. What do you think is the probability that the next flip is also a head? What if I had flipped the coin 100 times and each flip was a head?
TODO


### Question 3.12. You throw a fair coin one million times. What is the expected number of strings of 6 heads followed by 6 tails?

Important thing to note here that eventhough is that we don't have to bother about the overlap.

(Stolen from the solutions) Let $I_j$ be the indicator that is 1 if the sequece started in the $jth$ position. Then,

$$E(X) = E\left(\sum I_j\right) = \sum E\left(I_j\right)$$

There are 1000000-11 $I_j$'s thus we have

$$E(X) = \frac{10^6 - 11}{2^{12}}$$

#### What is the expected number of sequences of six tails, if we do not allow overlaps?
Not fully sure if this is correct but we can recycle the previous argument. 

If we would allow overlaps then we would have 

$$E(X) = \frac{10^6 - 5}{2^{6}}$$

But, the question is not 

#### What is the probability of getting at least one sequence of six heads followed by six tails? (very hard!)


### Question 3.14. A woman has two babies. One of them is a girl, what is the probability that the other is a boy?

$$P(B=1 | G\geq 1) = P(B=1\cap G\geq 1)/P(G\geq 1)$$
$$0.5/0.75 = 2/3$$

#### A dictator decides that to increase the number of sons in his realm, a family that has had a girl is allowed no more children. Would this work?

Intuitively we can see that every children as equal probability being a boy or a girl, thus, doesn't really matter the stopping condition that you have place the expected ratio will always be 50/50. 

You can all think it in the sense of a martingale. Let $D_i$ be the difference $B-G$ after the ith children of the family. Then, $D$ is a martingale, thus, $D_\tau$ where $\tau$ is the stopping time has expectation zero as well. 

Now assume every couple have a target number of children that the will have but if they have a girl before they reach their target then they will be having less children. 

So, if the goal is absolute numbers then it is counter productive since it would reduce the total number of children. And, since we already "showed" that the ration is expected to be balance it follows that the total number of boys is also reduced. 

#### Suppose there are three children, what's the probability all three are girls if one is?
$$P(G = 3 | G\geq 1) = \frac{P(G = 3 \cap G \geq 1)}{P(G \geq 1)} = \frac{1/8}{1 - 1/8} = 1/7$$

#### Suppose there are three children, what's the probability all three are girls if the middle child is a boy?
Clearly it is zero with both events are mutually exclusive. 

#### Suppose there are three children, what's the probability that two are girls if the middle child is a boy?
This is simply 1/4.

### Question 3.16. What is the probability that the fourth business day of the month is Thursday?
Add 5 business days start with 1/7 chance of being the ith business in a month. Now, the questions is to which day we allocate the extra 2/7th coming from the weekend. 

$$\begin{aligned}
1st \rightarrow Mon\\
2nd \rightarrow Tue\\
3rd \rightarrow Wed\\
4th \rightarrow Thu\\
5th \rightarrow Fri\\
\end{aligned}
$$

Thus, thursday with have a 3/7 of being the 4rth business day of the month. 

#### An event happens on business day k of the month. We want to minimise the number of times it happens on a Monday. What k do we choose? (We prefer smaller k if equal probability.)

Recycling the logic from above we have that 2, 3, 4, and 5 would give us 1/7 for monday. Thus, we brake ties and choose the 2nd business of the month. 

#### What is the probability that the third of January 2011 is a business day?

It is either zero or one since it is a deterministic event. 

#### What day of the week should we pick something to happen to minimise it happening on the fourth business day of the month?
We established that Thursday has the highest change to be the 4th business day of the month. Thus, anyother day should satisfy. 

We can start thinking about the distribution of holidays and go deeper in the estimation. 

### Question 3.17. You are playing Russian Roulette. There are precisely two bullets in neighbouring chambers of the six shooter revolver. The barrel is spun. The trigger is pulled and the gun does not fire. You are next, do you spin again or pull the trigger?

Bullets are heavy so they are likely to be in the bottom. But, lets ignore these. 

For starters the probability of having a bullet after a spin in 1/3. But, since they are consecutive it means that there are four empty chamber and only one of them has a bullet next. Thus, the chances of getting a bullet without a respin is 1/4. Thus, not respining the the correct way to go.

In general, we can see that if the revolver was 3 chambers then we respin, 4 we are indifferent and 5 and up we do not respin