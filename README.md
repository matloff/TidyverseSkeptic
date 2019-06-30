# TidyverseSkeptic
An opinionated view of the Tidyverse "dialect" of the R language.

## Norm Matloff, Prof. of Computer Science, UC Davis (former Prof. of Statistics at UCD)


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

### The claim

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

### Making learning harder, not easier

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

### Syntax comparison and teachability

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

The Tidyverse also makes heavy use of **magrittr** *pipes*, e.g. writing
the function composition **h(g(f(x)))** as

``` r
f(x) %*%  g() %*% h
```

Again, the pitch made is "English," in this case reading left-to-right.
And again, one might question just how valuable that is, but in any
event, personally tend to write such code left-to-right anyway,
*without* using pipes:

``` r
a <- f(x)
b <- g(a)
h(b)
```

And much more important, even advocates of pipes concede that pipes make
debugging more difficult.  And again, for large problems, piped code is
slower.

### Is dplyr needed or even desirable for teaching?

In discussions with those who report success in using the Tidyverse to
teach beginning programmers, I ask whether their students are incapable
of learning just base-R.  They readily concede that the answer is no.
Indeed, before the Tidyverse, throngs of people were learning base-R
without any prior programming background.

The Tidyverse advocates also claim that the "English" in **dplyr** makes
the code easier to read.  To me, that is missing the point; as any
instructor of software engineering can tell you, the best way to make
code readable is to use REAL English, in good, meaningful code comments.

Moreover, the Tidyverse can be difficult to debug, and run very slowly
on large datasets.

In short, in my view there is no advantage to teaching R through the
Tidyverse, and some significant disadvantages.

### The proper status of the Tidyverse in teaching

Again, I am certainly not saying one should only use base R; on the
contrary, CRAN is a major advantage of R, which I use extensively.
But the Tidyverse should be considered advanced R, not for beginners,
just as is the case for most complex CRAN packages.

# R's Status As an Open-Source Language

In the [SatRday LA conference](https://losangeles2019.satrdays.org/),
April 6, 2019, a speaker who was actually explaining the value of
**data.table** in large datasets said that package "was created by Matt
Doyle [sic].  Who's that?  No one knows who he is."  He repeated later,
"No one has ever heard of Matt Doyle."  Actually, many in the audience
had indeed heard of Matt Dowle, but in that speaker's world -- the 
RStudio-educated world" -- his statement about lack of name recognition
for Matt was sadly accurate.  Such is the huge and rapidly growing impact
of RStudio on R.

The reader may say, "If you don't like the Tidyverse, you don't have to
use it."  Sadly, that is not the reality here.  Hadley declared his
intention to essentially replace R with Tidy in his talk in the 2016
useR! conference.  The Tidyverse is a vigorous promotional effort by
RStudio that has come to dominate the R world.  As mentioned, it has
been especially active in the education realm.  

Given these dynamics, we will eventually, maybe rather soon, reach a
point at which most R users will be Tidy, and have indeed "Never heard
of Matt Dowle." This will make things very difficult for the non-Tidy R
people: Job seekers who are excellent R coders will find that they are
dismissed out of hand by Tidy interviewers; authors of non-Tidy CRAN
code will find their contribution is considered useless; academics
submitting research manuscripts or grant proposals will find that Tidy
reviewers give them low scores.  In short, R will have to bend to
RStudio's wishes.

As noted, I know and admire the people at RStudio, *but a commercial
entity should not have such undue, unilateral influence on an
open-source project.*  

It should be noted that neither Hadley nor anyone else one from RStudio
is in the elite, 20-member R Core Group, which controls the development
of the language.  The Tidyverse thus is tantamount to an *end-run around
the leaders of this open-source project*.  As any expert in
organizational behavior will tell you, this does not augur well for the
future health of R, in spite of undoubtedly being well-intentioned.

RStudio is a great company, staffed by many talented people.  In my
opinion, their one failing has been to run off on their own, rather than
adhering to the norms of open-source projects.  

In my view, RStudio can easily remedy the problem.  It can:

1.  Promote the teaching of base-R to beginners, treating the Tidyverse
    as an advanced topic.

2.  In the various RStudio Web pages on writing fast R code, give
    **data.table** equal time.
