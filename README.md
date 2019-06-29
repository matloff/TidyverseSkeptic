# TidyverseSkeptic
An opinionated view of the Tidyverse "dialect" of the R language.

### Norm Matloff, Prof. of Computer Science, UC Davis (former Prof. of Statistics at UCD)


Note:  This essay is somewhat blunt, and since it involves the
Tidyverse, is implicitly and sometimes explicitly about RStudio. I hope
it is polite and taken as constructive criticism.  

I like and admire the RStudio people, including the Tidyverse
originator, Hadley Wickham.  I have been interacting with them from the
beginning, when the firm consisted of only founder JJ Allaire and ace
developer Joe Cheng.  I highly praise the firm to my students, and I use
and recommend Hadley's **ggplot2** package (though I don't consider it
part of the Tidyverse).

Nevertheless, I believe that RStudio took a wrong turn when it decided
to promote the Tidyverse, which has led to a situation in which the very
health of the language is at stake.

[My bio is here.](http://heather.cs.ucdavis.edu/matloff.html)
Specifically in terms of R, I've been an R user and developer since near the 
beginning, having used R's predecessor S before that.  I've 
published several books that use R, and am currently (2019) the Editor-in-
Chief of the *R Journal*.

# Teachability

Teaching has been a keen interest of mine since my college days.
I've been a teacher of stat and computers for many years, and have
won various teaching awards, but it goes far beyond that; I really am
intensely interested in how people learn, from little kids to older
adults.  Among other things, I've taught English As a Second Language to
immigrant adults, most of whom have had less than a high school
education.

From this background, I strongly question the claim made 
by Tidyverse advocates that it facilitates the teaching
of R to beginning programmers.  There has been no study of this claim,
and I think the perceived success is psychological, a Bandwagon Effect.
On the contrary, I believe it is quite the opposite, i.e. using the
Tidyverse makes things more difficult for learners without prior
programming background.  

As noted, the students are being asked to learn a much larger volume of
material, which is clearly bad pedagogy.  See also ["The Tidyverse
Curse"](https://www.r-bloggers.com/the-tidyverse-curse), in which the
author says *inter alia* that he uses "only" 60 Tidyverse functions --
60!  The "star" of the Tidyverse, **dplyr** consists of over 400
functions, and while a user need not use more than a fraction of them,
the high complexity is clear.

Similarly, it is bad pedagogy to force students to learn tibbles, a
more complex technology, instead of data frames, a simpler one.

In discussions with those who report success in using the Tidyverse to
teach beginnng programmers, I ask whether their students are incapable
of learning just base-R.  They readily concede that the answer is no.
Indeed, before the Tidyverse, throngs of people were learning base-R
without any prior programming background.

Again, I am certainly not saying one should only use base R; on the
contrary, CRAN is a major advantage of R, which I use extensively.
But the Tidyverse should be considered advanced R, not for beginners,
just as is the case for most complex CRAN packages.

# Performance

As even RStudio concedes, the major components of the Tidyverse,
**dplyr** and **pipes**, can run very slowly compared to even base-R,
let alone the **data.table**, the non-Tidy alternative to **dplyr**
(which preceding the latter chronologically).  According to [a
study](http://www.win-vector.com/blog/2019/05/timing-working-with-a-row-or-a-column-from-a-data-frame/)
by the consulting firm Win-Vector, **dplyr** can be hundreds of times
slower than base-R, thus even worse relative to **data.table**.

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
