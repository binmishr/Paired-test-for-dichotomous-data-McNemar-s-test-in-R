# Paired-test-for-dichotomous-data-McNemar-s-test-in-R

Paired test for dichotomous data, McNemar’s test to see the effect of some treatment, training, or advertisement which brings about the changes in the attitude of individuals.

This test is mainly useful when the measurements are on the nominal or ordinal scale.

A McNemar’s test is used to compare the frequencies of paired samples when it has binary responses.

If your scale contains more than 2 levels then make use of Wilcoxon signed rank test
Hypothesis

Ho: There is no significant change in individuals after the treatment

H1: There is a significant change in individuals after the treatment

Let’s take a practical example in R
Getting Data

set.seed(345)
data <- data.frame(before = sample(c("Positive",
                                     "Positive",
                                     "Positive",
                                     "Positive",
                                     "Negative",
                                     "Positive",
                                     "Positive",
                                     "Positive",
                                     "Positive",
                                     "Negative",
                                     "Negative"),
                                   30, replace = TRUE),
                   after = sample(c("Positive",
                                    "Positive",
                                    "Positive",
                                    "Positive",
                                    "Negative",
                                    "Negative",
                                    "Negative",
                                    "Negative",
                                    "Negative",
                                    "Negative"),
                                  30, replace = TRUE))

A contingency table can be created based on table function:


Paired test Comparison

table(data$before, data$after) 
            Negative Positive
 Negative        4        6
   Positive      10       10
test <- mcnemar.test(table(data$before, data$after))

Paired test Output:-

McNemar's Chi-squared test with continuity correction
 data:  table(data$before, data$after)
 McNemar's chi-squared = 0.5625, df = 1, p-value = 0.4533

Conclusion

Based on McNemar’s test, the p-value is 0.45, above the 5% significance level and therefore the null hypothesis cannot be rejected.
