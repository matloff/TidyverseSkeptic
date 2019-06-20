# TidyverseSkeptic
An opinionated view of the Tidyverse "dialect" of the R language.

### Norm Matloff, Prof. of Computer Science, UC Davis; [my bio](http://heather.cs.ucdavis.edu/matloff.html)

(Work in progress.)

Note:  This essay is somewhat blunt, and since it involves the
Tidyverse, is implicitly and sometimes explicitly about RStudio
I hope it is polite and taken as constructive criticism.  I like and
admire the RStudio people, and have been interacting with them from the
beginning, when the first consisted of only founder JJ Allaire and
ace developer Joe Cheng.

R is rapidly devolving into two mutually unintelligible
dialects, ordinary R and the Tidyverse.  I, as a seasoned R programmer,
cannot read Tidy code, as it calls numerous Tidyverse functions that I
don't know.  Conversely, as one person in the Twitter discussion of this
document noted (approvingly), "One can code in the Tidyverse while
knowing very little R."

Note that, in using the term "Tidyverse," I am not including
pre-existing projects by Hadley Wickham, e.g. **ggplot2**, which I use a
lot and is not Tidy.  I also am not really including  **dplyr**, which
though Tidy, has similar functionality to Hadley earlier non-Tidy
version **plyr**. 

Instead, I am referring to things such as tibbles and
pipes.  I am especially concerned about the plethora of 
extra functions Tidyverse advocates burden students with learning, on
top of rudimentary base R.  These functions are unnecssary, as most can
be done simply in base R.

Though advocates claim it works well in teaching beginning programmers,
there has been no study of this claim, and I think the perceived success
is psychological, a Bandwagon Effect.  On the contrary, I believe it is
quite the opposite, i.e. using the Tidyverse makes things more difficult
for learners without prior programming background.  

As noted, the students are being asked to learn a much larger volume of
material, which is clearly bad pedagogy.  See also ["The Tidyverse
Curse"](https://www.r-bloggers.com/the-tidyverse-curse), in which the
author says *inter alia* that he uses "only" 60 Tidyverse functions --
60!  Similarly, it is bad pedagogy to force students to learn tibbles, a
more complex technology, instead of data frames, a simpler one.

Again, I am certainly not saying one should only use base R; on the
contrary, see my point above that CRAN is a major advantage of R.
But the Tidyverse should be considered advanced R, not for beginners,
just as is the case for most complex CRAN packages.

The Tidyverse is a vigorous promotional effort by a commercial entity
that has come to dominate the R world, RStudio.  I know and admire the
people at RStudio, *but a commercial entity should not have such undue
influence on an open-source project.*  

For instance, consider the lightning-fast **data.table** package. Rather
than welcoming it as a hugely valuable contribution to R, RStudio has
treated it as a competitor, downplaying it and promoting their own
product, **dplyr**.  This is simply not healthy for an open-source language.

In addition, all this is causing tension between some leaders in the two
camps.  All this does not augur well for the future of the language.

