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

## Problem 2

Using the local linear trend and seasonal effect was a bit tricky, but I was able to reproduce the results of the notebook shown. The steps involved taking the $CO_2$ data and using the 3 commands they used to get a model for the data. Then, I needed to look at their repository to get more insight into how theymade the predictions and gave the range of curves as well. Attempting to plot the standard of deviation away from the curve initially was not working as my scales and deviation exploded, but this was until I saw that I needed to train my samples for my prosterior function. This is not specific to the original source because even [the page on exploring the forefasting function uses it.](https://juanitorduz.github.io/intro_sts_tfp/).

Then after this, the last thing I tried to tackle ere deprecation warnings in the training code. My only headway was to change the optimizer to keras, as that the optimizer in the documentation was giving some of the deprecation warning. These warnings persisted though, so this code may not function forever. I do not need to import tensorflow with v2 compatibility though, as both implementations gave the warning.

If I wished to have a notebook give the same results everytime I could theoretically use a seed for my variational posterior and for the training. I also turned the iterations for reducing my loses to only 100, as the diminishing returns for higher iterations were not worth the extra wait times running my code. The year to train past can be altered as well, so I can predict what the a longer period of time. With minor alterations to the code, I could predict the $CO_2$ past the year 2018, but there would be nothing to compare it to to show validity of the method. Eitherway, I am satisfied with this code, I just wish that I could have understood what is still incompatible.