# David's Folder for Homework 9

## Problem 1

Calculating the probability that a person is actually infected by a disease given a positive test result is relatively straight forward. Using baye's theorem, you merely need the chance that a test is positive, a chance that you are infected overall, and the chance that a test will comeback positive if you are infected. However, the key difference between this classic paradox is that you are actually part of a pool of people, so now it is more ambiguous who would have caused the positive result. This leads to the single Baye's theorem:\
P(You are Infected | Pool is Positive) = P(Pool is Positive | You are infected)$\cdot$P(You are infected)/P(Pool is Positive).

Here, we cannot use the accuracy of a test for one person, because that is going to be different for different prevelances of the disease. We expect that the chances at least one person is infected in a pool goes to 100% if you take all the population.

The chance the pool will be positive will also need to be adjusted for the same reason, and so the updated chance of being infected should only increase for small pool sizes and converge to your positivity rate for large sample sizes.

I was able to find the specificity and the sensitivity of the type of Covid test UB uses (a drool test). I then found the positivity rate of both UB and the United States, and this just determines which population I am concluding about. Then, I use a binomial distribution to calculate the likelyhood that there are a specific number of infected in that group, and sum all the values (minus the chances 0 are infected).

I can then use this to find the chance that a pool is infected, and then I can use that information to find the accuracy of a pool test and the chances a pool will test positive in general.

A national average of 9.3% infected increases your chances to 12.69% if your pool of 12 tests positive.
UB's average of 0.46% updates your chances to 6.11%.
Eerie county's average of 1.1% updates your chances to 7.23%.

The notebook can be run for any number of people given any percentage of population has Covid, or any disease. Increasing the pool size to a large number takes your percentage back down to the original average because now the test is no longer able to tell you much about who was the one to cause the result.