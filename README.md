## CLEC
Incumbent local exchange carriers (ILECs), such as Verizon, install and maintain
local land-based telephone lines, lease capacity, and perform repairs for the
competing local exchange carriers (CLECs). The law requires that ILECs to
perform repairs in the same timely manner as that provided to their own
customers. The repair times (in hours) of 95 service requests from customers of
Verizon and 10 requests from customers of a CLEC during the same time period
were collected. The following code contains the collected data along with code
to perform an F-test on the data.

```r
# Data
ilec <- c(1,1,1,1,2,2,1,1,1,1,2,2,1,1,1,1,2,2,1,1,1,1,2,3,1,1,1,1,2,3,1,1,1,1,2,3,1,1,1,1,2,3,1,1,1,1,2,3,1,1,1,1,2,3,1,1,1,1,2,4,1,1,1,1,2,5,1,1,1,1,2,5,1,1,1,1,2,6,1,1,1,1,2,8,1,1,1,1,2,15,1,1,1,2,2) 

clec <- c(1, 1, 5, 5, 5, 1, 5, 5, 5, 5)

# Test statistic of ratio of variances with p-value
var_clec <- var(clec)
var_ilec <- var(ilec)

n_1 <- length(clec)
n_2 <- length(ilec)

observed_test_statistic <- var_clec / var_ilec
pf(observed_test_statistic, n_1 - 1, n_2 - 1, lower.tail = FALSE)
```

Suppose that Verizon wishes to compare the variability of repair times for ILEC
and CLEC customers. Consider the null hypothesis $H_0$: the population variance
of ILEC equals the population variance of CLEC.  Further, consider the test
statistic $F$ = (sample variance of CLEC) / (sample variance of ILEC).

This statistic follows an F distribution with degrees of freedom equal to
(sample size of CLEC - 1) and (sample size of ILEC - 1). For these data the
statistic for comparing the sample ratio of variances is 1.15 and the
corresponding p-value is 0.34. The p-value of this test is very sensitive to the
assumption that both populations are normally distributed. A viable alternative
that does not depend on the assumption of normality is a permutation test. To
compare this F-test and permutation test do the following:
    
   + Perform a one-sided permutation test on the ratio of variances. What is the
   p-value and what does it tell you?
   + What does a comparison of the two p-values say about the validity of the F
   test for these data?

## ACT
You are trying to decide between two ACT prep classes. Class 1 begins with a
general overview followed by an extensive number of practice exams. Class 2
covers each topic in depth with practice questions arranged by topic. Sample
data for each class is available in the file `act.txt` in your RStudio Cloud
Project. You can read this data into R using `read.table("act.txt", header =
TRUE)`. Based on a permutation test with 10,000 replications, does Class 1
increase ACT scores on average? Answer the same question for Class 2?  Write a
script named `act.R` or `act.Rmd` to address these questions. Underneath your
code, write a conclusion as to which class (or, neither class) you would
recommend. Justify your answers.


**There is no additional step necessary to turn in your homework. Simply create
the scripts described above and save your work in RStudio Cloud. Remember not
to edit or access your homework after the due date or it may be considered a
late submission.**
