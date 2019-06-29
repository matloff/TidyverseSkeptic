# TidyverseSkeptic
An opinionated view of the Tidyverse "dialect" of the R language.

### Norm Matloff, Prof. of Computer Science, UC Davis (former Prof. of Statistics at UCD)


Note:  This essay is somewhat frank, and since it involves the
Tidyverse, is implicitly and sometimes explicitly about RStudio. I hope
it is polite and taken as constructive criticism.  

I like and admire the RStudio people, including the Tidyverse
originator, Hadley Wickham.  I have been interacting with them from the
beginning, when the firm consisted of only founder JJ Allaire and ace
developer Joe Cheng.  I highly praise the firm to my students, and I use
and recommend Hadley's **ggplot2** package (though I don't consider it
part of the Tidyverse, having been developed well before Tidy).

Nevertheless, I believe that RStudio took a wrong turn when it decided
to promote the Tidyverse, which has led to a situation in which the very
health of the language is at stake.

[My bio is here.](http://heather.cs.ucdavis.edu/matloff.html)
Specifically in terms of R, I've been an R user and developer since near the 
beginning, having used R's predecessor S before that.  I've 
published several books that use R, and am currently (2019) the Editor-in-
Chief of the *R Journal*.

# dplry vs. data.table

The **dplyr** package, is a featured app of the Tidyverse developed by
Hadley, so I'll use this as an example at several points in this essay.

**Dplyr** borrowed a number of ideas from the earlier **data.table** by
Matt Dowle.  One of Hadley's major motivations was to give the user a
more "English-like" interface.

Unfortunately, **dplyr** is much, much slower than
**data.table** on large datasets.  Here are some of the
timing examples, for various operations, on the [H20 site]
(https://h2oai.github.io/db-benchmark/)
(in seconds):

<table border="1">
<tr>  <td>dplr</td>  <td>data.table</td>  </tr> 
<tr> <td>37.3</td>  <td>9.07</td> </tr>
<tr> <td>95.5</td>  <td>9.20</td> </tr>
<tr> <td>496</td>  <td>11.9</td> </tr>
</table>

The differences are even starker in
[this study](http://www.win-vector.com/blog/2019/05/timing-working-with-a-row-or-a-column-from-a-data-frame/)
by the consulting firm Win-Vec LLC, e.g.

![alt text](https://i0.wp.com/www.win-vector.com/blog/wp-content/uploads/2019/05/unnamed-chunk-1-2.png)

showing that **dplyr** can be extremely slow even relative to base-R,
thus even worse relative to **data.table**.

RStudio, a commercial entity, is heavily engaged in educational
activities, both with its own courses and in interacting with teachers
of R.  It has heavily promoted **dplyr**.  Meanwhile, RStudio and its
allies have typically ignored **data.table** in these promotions, e.g.
not mentioning it in their timing comparisons, and painting it as beyond
the reach of nonprogrammers.

RStudio is after all a for-profit business, so such treatment of
**data.table** is just good business practice.  But R is an open-source
language, and these actions have harmed R, as advocates of other
languages, notably Python, constantly denigrate R as being slow on large
datasets.

# Teachability

Teaching has been a keen interest of mine since my college days.  I've
been a teacher of stat and computers for many years, and have won
various teaching awards.  My book, *Statistical Regression and
Classification: from Linear Models to Machine Learning*, was the
recipient of the 2017 Ziegel Award.
 
But it goes far beyond that; I really am intensely interested in how
people learn, from little kids to older adults.  Among other things,
I've taught English As a Second Language to immigrant adults, most of
whom have had less than a high school education.

## The claim

From this background, I strongly question the claim made by Tidyverse
advocates that it facilitates the teaching of R to beginning
programmers, as opposed to teaching base-R.  (I regard both **dplyr**
and **data.table** as advanced topics; neither is suitable for
beginners.)

There has been no study of this claim.  Advocates often provide
testimonials from students like "I learned R using Tidyverse, and now am
productive in R!" -- which says nothing at all about the teachability of
base-R.  (It is ironic that advocates who present such statements are
statisticians, who ought to know the need for a control group.)

I think the perceived success is psychological.  There is a Bandwagon Effect
at work, and even a hint of cult-like behavior.
I've even seen statements on Twitter from "graduates" of Tidyverse
training who actually apologize because their code was not Tidy.

## Making learning harder, not easier

On the contrary, I believe it is quite the opposite, i.e. using the
Tidyverse makes things more difficult for learners without prior
programming background.  

As noted, the students are being asked to learn a much larger volume of
material, which is clearly bad pedagogy.  See also ["The Tidyverse
Curse"](https://www.r-bloggers.com/the-tidyverse-curse), in which the
author says *inter alia* that he uses "only" 60 Tidyverse functions --
60!  The "star" of the Tidyverse, **dplyr**, consists of over 400
functions, and while a user need not use more than a fraction of them,
the high complexity is clear.  Every time a user needs some variant of
an operation, she must sift through those hundreds of functions for one
suited to her current need.

Similarly, it is bad pedagogy to force students to learn tibbles, a
more complex technology, instead of data frames, a simpler one.

## Syntax comparison and teachability

Again, the claim is that the Tidyverse is more teachable because of its
"English-like" syntax, while they dismiss **data.table**'s syntax as
opaque.

.  Here is a comparison (adapted from
[here](https://atrebas.github.io/post/2019-03-03-datatable-dplyr/):
We'll use R's built-in **mtcars** dataset.

``` r
mtdt <- as.data.table(mtcars)
mtdt[cyl == 6]  # data.table syntax
mttb <- as_tibble(mtcars)
filter(mttb,cyl == 6)  # dplyr syntax
```

Is there really any difference?  Can't beginners, even without
programming background, quickly adapt to either one after seeing a few
examples?  As I said earlier, even those who claim high teachability for
**dply** do readily agree that their students could also easily pick up
**data.table**, or for that matter my preference base-R, given some
examples.

And what of the fact that we have the English word *filter* above?
Granted, it looks nice, but English can be misleading or mystifying in a
computer context.  Even an experienced programmer would not be able to
guess what the **dply** function **mutate()** does, for instance.

## Is dplyr needed for teaching?

In discussions with those who report success in using the Tidyverse to
teach beginning programmers, I ask whether their students are incapable
of learning just base-R.  They readily concede that the answer is no.
Indeed, before the Tidyverse, throngs of people were learning base-R
without any prior programming background.

## The proper status of the Tidyverse

Again, I am certainly not saying one should only use base R; on the
contrary, CRAN is a major advantage of R, which I use extensively.
But the Tidyverse should be considered advanced R, not for beginners,
just as is the case for most complex CRAN packages.

# R's Status As an Open-Source Language

R is rapidly devolving into two mutually unintelligible
dialects, ordinary R and the Tidyverse.  I, as a seasoned R programmer,
cannot read Tidy code, as it calls numerous Tidyverse functions that I
don't know.  Conversely, as one person in the Twitter discussion of this
document noted (approvingly), "One can code in the Tidyverse while
knowing very little R."

The Tidyverse is a vigorous promotional effort by a commercial entity
that has come to dominate the R world, RStudio.  As noted, I know and
admire the people at RStudio, *but a commercial entity should not have
such undue, unilateral influence on an open-source project.*  

Hadley declared his intention to essentially replace R with Tidy in his
talk in the 2016 useR! conference.  Yet neither he nor anyone else
one from RStudio is in the 20-member R Core Group, which controls the
development of the language.  The Tidyverse thus is tantamount to an
end-run around the leaders of this open-source project.  As any expert in
organizational behavior will tell you, this does not augur well for the
future health of R, in spite of undoubtedly being well-intentoned.

For instance, consider the lightning-fast **data.table** package. Rather
than welcoming it as a hugely valuable contribution to R, RStudio has
treated it as a competitor, downplaying it and promoting their own
product, **dplyr** (which came later than **data.table**).  Again,
this is simply not healthy for an open-source language.

In my view, RStudio can easily remedy the problem, by promoting the
teaching of base-R to beginners, treating the Tidyverse as an advanced
topic.
