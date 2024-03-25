# Quant Job Interview Notes
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


|      | **1** | **2** | **3** | **4** | **5** | **6** |
|---|---|---|---|---|---|---|
| **1** |  2  |  3  |  4  |  5  |  6  |  7  |
| **2** |  3  |  4  |  5  |  6  |  7  |  8  |
| **3** |  4  |  5  |  6  |  7  |  8  |  9  |
| **4** |  5  |  6  |  7  |  8  |  9  | 10  |
| **5** |  6  |  7  |  8  |  9  | 10  | 11  |
| **6** |  7  |  8  |  9  | 10  | 11  | 12  |


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


### 3.6. Suppose we toss a fair coin, and let N denote the number of
tosses until we get a head (including the final toss). What is E(N) and Var(TV)?