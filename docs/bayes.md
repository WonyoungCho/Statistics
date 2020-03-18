# Bayesian updating
- <https://ocw.mit.edu/courses/mathematics/18-05-introduction-to-probability-and-statistics-spring-2014/readings/>
```
Example 4. A screening test for a disease is both sensitive and specific. By that we mean
it is usually positive when testing a person with the disease and usually negative when
testing someone without the disease. Let’s assume the true positive rate is 99% and the
false positive rate is 2%. Suppose the prevalence of the disease in the general population is
0.5%. If a random person tests positive, what is the probability that they have the disease?
answer: As a review we first do the computation using trees. Next we will redo the
computation using tables.
Let’s use notation established above for hypotheses and data: let H+ be the hypothesis
(event) that the person has the disease and let H− be the hypothesis they do not. Likewise,
let T+ and T− represent the data of a positive and negative screening test respectively. We
are asked to compute P(H+|T+).

We are given
P(T+|H+) = 0.99, P(T+|H−) = 0.02, P(H+) = 0.005.
From these we can compute the false negative and true negative rates:
P(T |H− +) = 0.01, P(T |H− −) = 0.98
All of these probabilities can be displayed quite nicely in a tree.

Bayes’ theorem yields
P(H+|T+) = P(T+|H+)P(H+)/P(T+) = (0.99 · 0.005) / (0.99 0.005 + 0.02 0.995) = 0.19920 ≈ 20%

Now we redo this calculation using a Bayesian update table:

                              Bayes
hypothesis prior likelihood numerator posterior
H   P(H)  P(T+|H) P(T+|H)P(H)   P(H|T+)
H+  0.005   0.99    0.00495     0.19920
H−  0.995   0.02    0.01990     0.80080
total 1    NO SUM   0.02485        1

The table shows that the posterior probability P(H+|T+) that a person with a positive test
has the disease is about 20%. This is far less than the sensitivity of the test (99%) but
much higher than the prevalence of the disease in the general population (0.5%).
```
