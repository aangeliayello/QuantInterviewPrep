# Quant Job Interview Notes
## Intro

## Option Pricing
PH

## Probability

### Question 3.1. Consider the following game. The player tosses a die once only. The payoff is 1 dollar for each dot on the upturned face. Assuming a fair die, at what level should you set the ticket price of this game?

Here, we just take the expected value of the payoff. 

$$E(D) = \frac{1}{6} ( 1 + 2 + ... + 6) = 3.5$$

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