# Teaching R in a Kinder, Gentler, More Effective Manner: 

## Teach Base-R, Not Just the Tidyverse  

## Prof. Norm Matloff, University of California, Davis; January 11, 2023

# Prologue

Recently an R user 
[tweeted](https://twitter.com/adamTford/status/1611520259579871232)
sardonically,

> I want to replace the value in a cell in something the kids are calling
> a 'tibble'. In baseR, it was a simple 1 liner for a dataframe:
> 
> df[column#,row#]=newvalue
> 
> What's the Tidy version?

The stark answer is that **there really is no good Tidy way to do this
very basic, fundamental operation in R,** something that a base-R course
would treat in the first lesson or two.  Clearly:

> There is something very wrong with the Tidy(-only) approach to teaching R
> learners.

# Overview:  Teaching R to Noncoder Learners 

The context of this essay is how to teach R to students without prior
coding background.  These learners typically come from the social sciences,
business, or the humanities, sometimes from the life sciences.

**I believe that teaching R via the Tidyverse is counterproductive
for this group of learners.**

* The Tidyverse is more complex and abstract than base-R, hence **harder
  to learn**, directly antithetical to Tidy's stated goal of making R
accesible to a broader community.

* Tidy-based courses must therefore restrict coverage to a small set of
  operations, mainly a few **dplyr** verbs.  The students may be happy
but they are **unprepared to use R productively in their work,** as
exemplified in the above tweet, 

* Accordingly, noncoder learners should be taught a mix of base-R and
  Tidy, starting first with base-R.  "Graduates" of mixed courses are
  then equipped to apply whichever tool they find most convenient in any
  given application.

Note:  By "base-R" I mean array indices, loops, if-then-else and so on.
I do NOT advocate a slow, boring approach in which, for instance, one
starts with "R data can be real, character or logical..."  My own
[online course](https://github.com/matloff/fasteR) has students doing
useful operations starting in the very first lesson.

# Where I'm Coming From

What informs my views here?

I teach in the Computer Science Dept. at UC Davis (though again, my
focus here is on noncoder learners of R, not CS majors).  I formerly was
a Professor of Statistics at that university. I am an award-winning
textbook author, and am also the recipient of university awards for
teaching and public service. 

Specifically in terms of R, I have been an R user and developer since
near the beginning, having used R's predecessor S before that.  I've
published several books that use R, and have served as the
Editor-in-Chief of the *R Journal*, as well as Associate Editor for the
*Journal of Statistical Software*. My abovementioned R tutorial for
beginners, [fasteR](https://github.com/matloff/fasteR), has become my
most popular GitHub repo, with nearly 700 GitHub stars.

But it goes far beyond that; I really am intensely interested in how
people learn, from children to middle-aged adults. Among other things,
I've taught English As a Second Language to working-class adults from
China, and have taught a short course on probability to sixth-graders.

See my [full bio](https://heather.cs.ucdavis.edu/matloff.html)

# Preliminaries

## The main issue is how to teach R learners to do data analysis

Note that in discussing teaching in this essay, I am taking the target
audience here to be **nonprogrammers** who wish to use R for data
analysis.  

## Note on ggplot2 re marketing

RStudio's presentation of **ggplot2** as part of the Tidyverse is
misleading.  That package predates Tidy, and the package is widely used
by both base-R advocates and Tidy proponents alike.  RStudio's marketing
of Tidy as including **ggplot2** only came later.

This is important, since many who praise Tidy cite **ggplot2** as their
first reason for being pro-Tidy in teaching.  This obfuscates the real
problems with Tidy as I see them:

* focus on **dplyr**, **purrr** and pipes, and 

* a ban/near ban on the use of loops, the '$' sign, brackets

More details [later in this document](README.md#ggplot2-versus-the-tidyverse).

## The Purist R Teachers

I believe that R learners should be taught both base-R and Tidy, base-R
first.  Many R teachers feel the same way.  But there are some who:

* Refuse to teach any base-R.

* Ban the use of $, [, loops, the apply() family and so on.

* Treat **dplyr** as the go-to tool for almost any R action, including
challenging ones, ignoring that base-R might lead to a simpler solution.
Again, the example in the Prologue above illustrates this.

# Kudos to RStudio, but they took a wrong turn

(As of July 2022, RStudio changed its name to Posit, but in this
document I will use the original, more familiar name.)

I like and admire the RStudio people, including the Tidyverse
originator, Hadley Wickham, and have always supported them, both
privately and
[publicly](https://matloff.wordpress.com/2018/02/22/xie-yihui-r-superstar-and-mensch/).
They and I have been interacting from the beginning, when the firm
consisted only of founder JJ Allaire and ace developer Joe Cheng.  I
highly praise the firm to my students, and I use and recommend 
Hadley's (NON-Tidyverse) packages **ggplot2** and **stringr**. 
On occasion his **devtools** has been an absolute lifesaver for me.
Hadley was the internal reviewer for my book, *The Art of R
Programming*, and I was one of the internal reviewers for Hadley's
*Advanced R* (2nd. ed.).  RStudio's **Quarto** package is an exciting
new development for the R community.

Nevertheless, I believe that **RStudio took a wrong turn when it decided
to promote the Tidyverse** for beginning learners who have no prior
coding background.  Tidy makes it more difficult for noncoders to learn
R, and leaves them less able to use it productively.  

RStudio has always been a very public-spirited firm (they eventually
changed to Public Benefit Corporation legal status),   In this light,
it is very unfortunate that **RStudio did not consult with the broader
R community in developing this new "dialect" of R.**

As noted in my background summary above, I have been quite active in the
R movement, so all this  is quite troubling to me.  Hence the document
you are now reading.

# Teachability Overview--Tidy Is Overly Complicated and Poorly Equips Students for Practical Use

* Again, my focus here is on teaching R to those with little or no
coding background.  I am *not* discussing teaching Computer Science
students. 

* Tidy was consciously designed to equip learners with just a small set
of R tools.  The students learn a few **dplyr** verbs well, but that
equips them to do much less with R than a standard R beginners course
would teach.  That leaves the learners **less equipped to put R to
practical use**, compared to "graduates" of standard base-R courses.

* Tidy teachers of R claim great success, but **these "testimonials"
  are misleading.**  The "success" is due to watering down the material
(and conflation with **ggplot2**).  The students learn to mimic a few
example patterns and may be happy, but they are not equipped to use R
beyond superficial operations.

* The Tidyers' refusal to teach the '[' and [ '$' operators, and the
lack of coverage of R vectors, are major handicaps for Tidy
"graduates" to making use of most of R's **statistical functions and
statistical packages.**  

* Tidy's is **too abstract** for noncoder beginners, due to the
  philosophy of functional programming (FP). The latter is popular with
many sophisticated computer scientists, but is **difficult even for
computer science students, let alone the nontech learners** that form our
focus here.  Tidy is thus unsuited as the initial basis of instruction
for nonprogrammer students of R.  FP should be limited and brought in
gradually.  The same statement applies to base-R's own FP functions.

* The Tidy FP philosophy replaces straightforward, easily grasped, loops
with abstract use of functions. Since functions are the most difficult
aspect for noncoder R learners, FP is clearly not the right path for
such learners.  Indeed, even many Tidy advocates concede that it is in
various senses often **more difficult to write Tidy code than base-R**. Even
Hadley says, for instance, "it may take a while to wrap your head around
[FP]."

* A major problem is **Tidy's cognitive overload**: The
basic operations contain myriad variants. Though of course one need
not learn them all, one needs some variants even for simple operations,
e.g. pipes on functions of more than one argument.

* The obsession among many Tidyers that one must avoid writing loops,
the '$' operator, brackets and so on often results in obfuscated code.
Once one goes beyond the simple **mutate/select/filter/summarize**
pattern, Tidy programming can be of low readability.  **The much-vaunted
"English-like" theme of Tidy becomes an obstacle rather than an aid**.

* Tidy advocates also concede that **debugging Tidy code is difficult**,
especially in the case of pipes. Yet noncoder learners are the ones
who make the most mistakes, so it makes no sense to have them use a
coding style that makes it difficult to track down their errors.

In summary, Tidy uses unnecessarily complicated machinery, an obvious
drawback for teaching beginners, and yet only equips students to perform
a narrow set of operations.  It would be like teaching English As a
Second Language as follows:  The instructor teaches the students to say
"Good Morning," by providing them with a template like,

> It is my fervent wish that you find your morning unusually fulfilling.

The students would be told to substitute *morning* with *afternoon* or
*evening*.  But they would have no idea what the other words mean, and
it would not generalize much.  The students may even rave about these
English "lessons," but they won't have learned much at all.


# Examples

*Case study: delayed learning (I)*

Let's look at an example in my online R tutorial,
[**fasteR**](http://github.com/matloff/fasteR).  Consider, for
instance, an innocuous line like 

``` r
> hist(Nile)
```

i.e. drawing a simple histogram of R's built-in Nile River dataset.  

This is in the very first lesson in my tutorial.  Easy!  By contrast,
the Tidy crowd forbids use of base-R plots, insisting on using
**ggplot2**.  I also prefer **ggplot2** to base-R graphics (though again
it should not be considered part of the Tidyverse), but
here we have a much more important goal--to give students an actual
useful application of R right from the start.  Tidy greatly impedes that
goal.

To be Tidy the instructor would have to do something like

``` r
> library(ggplot2)
> dn <- data.frame(Nile)
> ggplot(dn) + geom_histogram(aes(Nile),dn)
```

Here the instructor would have a ton of things to explain -- packages,
data frames, **ggplot()**, the **aes** argument, the role of the '+'
(it's not addition here) and so on -- and thus she could definitely NOT
present it in the first lesson.

(Things would be simpler for Tidy instructors if they were to use
**qplot()** in the **ggplot2** package, but as far as I know, few if any
Tidy courses do this.)

Also in my very first lesson, I do

``` r
> mean(Nile[80:100])
```

printing the mean Nile River flow during a certain range of years.
Incredibly, not only would this NOT be in a first lesson with Tidy, the
students in a Tidy course may actually *never* learn how to do this.
Typical Tidyers don't consider vectors very important for learners, let
alone vector subscripts. 

As a concrete example of this Tidy point of view, consider the book
*Getting Started with R*, by Beckerman *et al*, Oxford University Press,
second edition, 2017.  The book makes a point of being 
["Tidyverse compliant"](https://twitter.com/GSwithR/status/996830294367002625).
In 231 pages, vectors are mentioned just briefly, with no coverage of 
subscripts.  Hadley, in his Tidy "bible," *R for Data Science", actually
does cover vectors--but not until Chapter 20.*  Again, typical Tidy
courses don't cover vectors at all.

In other words, **even after one lesson, the base-R learner would be way
ahead of her Tidy counterparts.**

*Case study: delayed learning (II)*

A researcher tweeted in December 2019 that an introductory statistics
book by Peter Dalgaard is "now obsolete," because it uses base-R rather
than Tidy.  Think of what an "update" to use of Tidy would involve, how
much extra complexity it would impose on the students.  Here is an early
lesson from the book:

``` r
> thue2 <- subset(thuesen,blood.glucose < 7)
```

This could easily be in the base-R instructor's second lesson, if not
the first.  For Tidy, though, this would have to be changed to

``` r
> library(dplyr)
> thue2 <- thue2 %>% filter(blood.glucose < 7)
```

Here the instructor would first have to teach the pipe operator '%>%',
again extra complexity.  And in so doing, she would probably emphasize
the "left to right" flow of pipes, but the confused students would then
wonder why, after that left-to-right flow, there is suddenly a
right-to-left flow, with the '<-'.  (For some reason, the Tidy people
don't seem to use R's '->' op.)

Again, the Tidyverse is simply too complex for R learners without coding
background.  **It slows down their learning process.**

*Case study:  tapply() (I)*

One of the most commonly-used functions in base-R is **tapply()**.  It's
quite easy to teach beginners, by presenting its call form to them:

``` r
tapply(what to split, how to split it, 
   what to apply to the resulting chunks)
```

However, for some reason Tidy advocates deeply resent this function.
Indeed, **tapply()** epitomizes what's wrong with base-R.  

When the Tidyverse was first developed, Prof. Roger Peng gave a
thoughtful keynote talk, *Teaching R to New Users--from tapply to the
Tidyverse*, also presented as [a Web
page](https://simplystatistics.org/posts/2018-07-12-use-r-keynote-2018/).
Oddly, **tapply()** is not mentioned in Dr. Peng's talk or in the
printed version, but the title says it all:  One should teach Tidy, not
**tapply()**.

Surprisingly, though, in making his comparison of Tidy to base-R, his
base-R example is **aggregate()**, not **tapply()**.  The complexity of
**aggregate()** function makes for an unfair comparison, a straw man; 
**tapply()** is much simpler, and perfect for R beginners, and thus the
proper comparison as the title of the talk seems to agree).(

Below is an example from the Peng talk, using the built-in R dataset
**airquality**.  We find the mean ozone level by month:

``` r
group_by(airquality, Month) %>% 
   summarize(o3 = mean(Ozone, na.rm = TRUE))
```

Here is the base-R version offered by Dr. Peng:

``` r
aggregate(airquality[, “Ozone”], 
      list(Month = airquality[, “Month”]), 
      mean, na.rm = TRUE)
```

Indeed, that base-R code would be difficult for R beginners.
But here is the far easier base-R code, using **tapply()**:

``` r
tapply(airquality$Ozone,airquality$Month,mean,na.rm=TRUE)
```

This fits clearly into our **tapply** call form shown above:

* What to split: Ozone

* How to split it: by Month

* What to apply to the resulting chunks: mean

The Tidy version requires two function calls rather than one for base-R.
The Tidy code is a bit wordier, and requires that one do an assignment
(to **o3**).  All in all, **the base-R version is simpler, and thus easier
for noncoder beginners**.

*Case study:  tapply() (II)*

Of course, one can find instances in which each approach, base-R and
Tidy, is simpler to use than the other.  Indeed, I have strongly
advocated that noncoder R learners should pick up some of both.  (Much
more on this point below.)  But I think it's worth repeating how simple it is
for R learners to solve many basic problems using **tapply()**.

Consider this example, a bit more advanced, that I like to use to
motivate linear regression models.  We wish to predict human weight from
height, and wish to first check approximate linearity. 

The dataset, involving heights and weights of professional baseball
players, **mlb**, is from my **regtools** package.  For each height
value, there are various players of that height, so 
we plot mean weight against height, checking for a linear pattern.  

Base-R:

``` r
htsAndWts <- tapply(mlb$Weight,mlb$Height,mean)        
plot(htsAndWts)
```

Tidy (plus **ggplot2**):

``` r
mlb %>% 
group_by(Height) %>% 
summarize(weights = mean(Weight)) %>%              
ggplot(aes(x=Height,y=weights)) + geom_point()                
```

Two major **dplyr** functions, pipes, and a somewhat sophisticated usage
of **ggplot2**!  It would be out of the question to use this example
early in a Tidy course, far too much machinery to cover.  But easy to do
so in a course using base-R, in the first or second lesson.  That should
be the goal, empowering students to work on real problems, early on.

# Dogmatic Teaching Is Harmful to Students

Most people, on most issues, avoid extremes.  But some teachers of R
have gone polemic, with dogmatic calls for "purity," with a Tidy-only
approach.

I did suggest a mixed approach to RStudio founder and CEO JJ Allaire
when we met (at his request) in 2019.  Unfortunately, JJ did not like
the idea either, on the grounds that RStudio should not be telling
people how to teach.  But of course, that is exactly what RStudio has
been doing in promoting Tidy.

I'll take for my examples here from the [*Educator's Perspective*
article](https://escholarship.org/uc/item/7kk4d922), written by a number
of prominent Tidy advocates.  The authors' viewpoint is commonplace in
the US.

## No dollar sign allowed, no brackets, no loops, even no lm() 

The Tidyers believe that two of the most basic operations in R,
the \$ sign and bracketing, are harmful.  For instance, consider an
example in *Educator's Perspective*.

The dataset is loan data available in the **openintro** package.  Here
is the Tidy code to preprocess the data:

``` r

loans <- openintro::loans_full_schema %>%
   mutate(
         homeownership = str_to_title(homeownership),
         bankruptcy = if_else(public_record_bankrupt >= 1, "Yes", "No")
         ) %>%
   filter(annual_income >= 10)

```

In base-R:

``` r

loans <- openintro::loans_full_schema
loans$bankruptcy <- ifelse(loans$public_record_bankrupt >= 1, "Yes", "No")
subset(loans,annual_income >= 10)

```

One should not conflate conciseness with clarity.  But
here the base-R code is both more concise *and* more straightforward.
The Tidyers might even agree, except that they would object to
the code's usage of '$'.  As the article puts it:

> When using base R the variables in that data frame are commonly
> accessed with the $ operator (e.g., loans$loan amount to access the
> variable called loan amount in the data frame loans). Often, students
> are tempted to access the loan amount variable in this example by
> referring to it simply as loan amount and not specifying the name of
> the data frame in which it lives. This results in a frustrating error:
> object 'loan amount' not found.

The simple solution to this "problem" is to explain it to students, and
have them watch for it.  It would be impossible to have students avoid
all possible errors, and again, this one is easy to remedy with proper
advance warning.  Isn't this preferable to saddling learners with are
more complex, less direct coding paradigm?  Don't "throw the baby out
with the bath water"!

And the argument "Coding style X often results in errors by beginners,
so we should replace X by other machinery" of course works both ways.  A 
common error among Tidy beginners is failure to reassign the result of
something like **mutate()**.  The above argument would imply that the
base-R approach of simply tacking on the new variable to the given data
frame is superior, as we did in the code above,

``` r
loans$bankruptcy <- ifelse(loans$public_record_bankrupt >= 1, "Yes", "No")

```

Tidy essentially ignores vectors.  Consider this very simple example:
Say we wish to add to the **mtcars** data a column consisting of the
horsepower-to-weight ratio.

In base-R, it is extremely simple:

``` r
   mtcars$hwratio <- mtcars$hp / mtcars$wt
```

Want to add a column to a data frame?  Hey, just add it!

But in Tidy:

``` r
   mtcars %>% mutate(hwratio=hp/wt) -> mtcars
```

Still not terribly complex, but again  we're invoking some machinery --
piping, a function call, and reassigning to the original data frame  The
base-R version is simple and straightforward, thus easier for R
beginners to grasp.

The Tidyers oppose teaching loops to beginners, again on the grounds that loop
coding is error-prone.  That is open to debate, but the point is that
loops are easier to debug; the sophisticated machinery that Tidyers want
in lieu of loops, FP, is NOT easy to debug (more on this below).  Here
the Tidyers' "cure is worse than the disease.".

The article is so purist that it even recommends against teaching 
**lm()**.  Use **broom**, they say.  What's next, a Tidy wrapper for
**sqrt()**?

## "dplyr or bust"

The Tidyers become so focused on Tidy that they try to solve every
problem by using that tool.  The result is seen in "How do I do
such-and-such using Tidy?" queries in Twitter, Stack Overflow and so on.

In many cases, the problem has a simple and direct base-R solution, but
those who submit the queries are so fixated on **dplyr**, that they are
incapable of taking that easier path.

*Case study:  Hadley and tapply()*

As noted earlier, many who learned R from a Tidyer are surprised to
learn that **ggplot2** makes liberal use of **tapply()**.  It shouldn't
be surprising, as **ggplot2** is pre-Tidy, but many of the more ardent
Tidyers have portrayed **tapply()** as the epitome of "What's wrong with
R."

The tragic error of the "**dplyr** or bust" obsession is shown in the following
Twitter exchange.

David Robinson, a well-known Tidy advocate, 
[tweeted](https://twitter.com/drob/status/766294758696357888?language=en)

dplyr #rstats pattern I use constantly:

> %>%
>   group_by(...) %>%
>   mutate(n = n()) %>%
>   ungroup()
> 
> Do others? Would a shortcut be helpful?

Hadley correctly replied, in
[the same thread](https://twitter.com/hadleywickham/status/766301706103554048),
that one should use base-R functions here, **ave()** or **tapply()**.

An R Core member, commenting on this phenomenon (but not this incident)
cited a saying, "Sometimes the followers are holier than the prophet." 


## Poor readability, unnecessary cognitive overload

As noted, R courses using the Tidyverse often do rather little beyond
their canonical *data %>% group_by %>% mutate %>% summarize* paradigm.
That leaves the learners less equipped to put R to practical use, compared to
"graduates" of standard base-R courses.

Even more important, once one gets past that simple paradigm, Tidy runs
into real problems.

Again, let's use an **mtcars** example taken from
[an online tutorial](https://towardsdatascience.com/functional-programming-in-r-with-purrr-469e597d0229).  Here the goal is to regress miles per gallon against weight, calculating R<sup>2</sup> for each cylinder group.  Here's the Tidy
solution, from the online help page for **map()**:

``` r
mtcars %>%
  split(.$cyl) %>%
  map(~ lm(mpg ~ wt, data = .)) %>%
  map(summary) %>%
  map_dbl("r.squared")

#  output
4         6         8 
0.5086326 0.4645102 0.4229655
```

There are several major points to note here:

* The R learner here must learn two different FP map functions for this
  particular example.  This is an excellent example of Tidy's cognitive 
  overload problem.  Actually, the Tidyverse FP package, **purrr**, has 
  52 different map functions!  (See below.)

* That "Tidy" code is a nightmare to read.  For instance, 
  the first '~' in that first map call is highly nonintuitive.  This
  is starkly counter to the Tidyers' claim that Tidy is more intuitive and
  English-like.

* Tidy, in its obsession to avoid R's standard '$' symbol, is causing
  all kinds of chaos and confusion here.

The hapless student would naturally ask, "Where does that expression
'summary' come from?"  It would appear that **map()** is being called on
a nonexistent variable, **summary**.  In actuality, base-R's **summary()** 
function is being called on the previous computation
behind the scenes.  Again, highly nonintuitive, and NOT stated in the
online help page.

The poor student is further baffled by the call to **map_dbl()**.
Where did that 'r.squared' come from?  Again, Tidy is hiding the
fact that **summary()** yields an S3 object with component **r.squared**.  Yes,
sometimes it is helpful to hide the details, but
not if it confuses beginners.

The fact is, **R beginners would be much better off writing a loop here,
avoiding the conceptually more challenging FP.** But even if the
instructor believes the beginner *must* learn FP, the base-R version is
far easier:

``` r
lmr2 <- function(mtcSubset) {
   lmout <- lm(mpg ~ wt,data=mtcSubset)
   summary(lmout)$r.squared
}
u <- split(mtcars,mtcars$cyl)
sapply(u,lmr2)
```

Here **lmr2()** is defined explicitly, as opposed to the Tidy version, with
its inscrutable '~' within the **map()** call.

In a [Twitter discussion](https://twitter.com/dgkeyes/status/1200532987000971264)
of the above example, a Tidy advocate protested that the above **purrr** code was not 
appropriate for learners:

> Sure, but my original tweet was about teaching newbies. Your example is
> not really relevant to that because it's about a VERY complex concept.

Exactly my point!  **Newbies should write this as a plain loop, NOT using
purrr** or even base-R's FP constructs.  Then it won't be advanced at
all.

But the Tidy promoters don't want learners to use loops.
So the instructor using Tidy simply would avoid giving students such an
example, whereas it would be easy for the base-R instructor to do so.

Granted, loops can lose their clarity if they are nested.  This can be
ameliorated by using good comment lines and indenting, but it's fine to
use functions---not in FP format, but simply as calls.  For learners,
Use the format

``` r
for (outer loop specs) {
   ...
   w <- f(whatever)
   ...
}

f <- function(something) 
{
#  the work of what would have been the inner loop goes here
}
```

rather than say, one of the **apply()** or **purrr** functions.

**Again, Tidy has a serious problem of cognitive overload.** Tidyverse
students are being asked to learn a much larger volume of material.
This is ironic, in that the goal in developing Tidy for teaching was
to limit a course to just a few verbs.  The problem is that the verbs
have dozens of variants.  This is clearly bad pedagogy.  

Tidy advocates say the uniformity of interface in all those functions
makes learning them easier.  Uniform *syntax* is nice, yes, but the fact
remains that users must learn the *semantics* of the functions, i.e.
what operations they perform.  What, for example, is the difference
between **summarize()**, **summarize_each()**, **summarize_at()** and
**summarize_if()**?  Under which circumstances should each be used?  The
user must sift through this.

As Matt Dowle, creator of **data.table**, [pointed
out](https://twitter.com/MattDowle/status/1142001162230489088) about
**dplyr**,

> It isn't one function **mutate** that you combine in a pipe.  It's
> **mutate**, **mutate_**, **mutate_all**, **mutate_at**, **mutate_each**,
> **mutate_each_**, **mutate_if**, **transmute**, **transmute_**,
> **transmute_all**, **transmute_at** and **transmute_if**.  And you're
> telling me [because of consistency of the user
> interfaces] you don't need a manual to learn all those?

Having a common syntax thus does not compensate for this dizzying
complexity. 

And students who need to go further will find a daunting task.  See
["The Tidyverse Curse"](https://www.r-bloggers.com/the-tidyverse-curse),
in which the author says *inter alia* that he uses "only" 60 Tidyverse
functions -- 60!  The "star" of the Tidyverse, **dplyr**, consists of
263 functions. 

While a user initially need not use more than a small fraction of those
263 functions, the high complexity is clear.  Every time a user needs
some variant of an operation, she must sift through those hundreds of
functions for one suited to her current need.  

By contrast, if the user knows base-R (not difficult), she can handle
any situation with just a few simple operations.  The old adage applies:
"Give a man a fish, and he can eat for a day. Teach him how to fish, and
he can eat for a lifetime."  

Note that the above example uses the "dot notation," used when the
output of a pipe is fed into a multi-argument function.  Here is the
[advice](https://magrittr.tidyverse.org/reference/pipe.html) given at
the official Tidyverse site:

> Placing lhs elsewhere in rhs call
> 
> Often you will want lhs to the rhs call at another position than the
> first. For this purpose you can use the dot (.) as placeholder. For
> example, y %>% f(x, .) is equivalent to f(x, y) and z %>% f(x, y, arg =
> .) is equivalent to f(x, y, arg = z).

This phrasing is likely beyond the comprehension of many R beginners.
Seeing a few examples would help them, of course. but it is yet another
example of how Tidy causes cognitive overload for learners.

# Tidy As an Obstacle to R Statistical Methods

As noted above, some Tidyers even oppose teaching **lm()**.
Instead, they recommend using the **broom** wrapper.  The wrapper is
indeed useful, but students need to learn the basics.  And of course, it
is unreasonable to ask that the hundreds of R statistical operations,
and the thousands of packages, all have Tidy wrappers.

Consider the Tidyers' opposition to teaching the '$' and brackets
operations.  This is an obvious impediment to using R's statistical
operations.  

Most of the R statistical functions return S3 objects, i.e. lists,
accessible via '$'.  Similarly, statistical operations in R are mainly
vector- and matrix-oriented.  (A matrix is a special case of a vector.)
I would find it difficult to teach a course in linear regression,
principal components, log-linear models and so on to students who did
not have solid prior experience with '$' and vectors.

Thus we immediately see a problem with Tidy:  It creates a barrier to
use of R as a statistical tool by Tidy "graduates."

[Here](https://clauswilke.com/blog/2020/09/07/pca-tidyverse-style/) is
an example of bridging the gap between Tidy and statistics, by Claus
Wilke, who begins by reporting, "I’ve finally figured out how to perform
a PCA using the tidyverse."  His word "finally" shows that there is
indeed a gap.  His answer is to use the **broom** package.  As it was,
even that package did not quite work, he said, though the development
version did.  And what about the thousands of CRAN packages that return
S3 objects?  Is **broom** going to provide a Tidy interface to each one?
That of course would be unrealistic.

A fundamental problem, from my point of view, is that the RStudio people
are not primarily statisticians.  Their focus is on developing software,
primarily for data wrangling and graphics.  They do this quite well, but
they are not the types who sit around debating, for example, the
propriety of p-values.  Statistics is not foremost on their radar
screens, and this sad gap between Tidy and statistics is a result.

# Tidy Obstacles to Debugging

Here is an example from *Text Mining with R*, by Julia Silge of RStudio,
and the aforementioned David Robinson. It's a great introduction to the
text analysis field, and I myself have found the book useful.  

This example, which may be found
[here](https://cran.r-project.org/web/packages/tidytext/vignettes/tidytext.html),
is a bit more involved than the previous ones, and thus better
illustrates my concerns about debugging Tidy code.  Courses that teach
using Tidy do very well for simple examples; this one is more complex,
possibly in terms of writing the code, and definitely in terms of
debugging.

Debugging is something I've given a fair amount of thought to.  I even
wrote a book on it, *The Art of Debugging* (NSP, 2008).  As noted
earlier, noncoder R learners are the ones most in need of debugging
skills, as they make the most errors.  Thus the example here is of high
importance.

The R package **janeaustenr** brings in full corpuses of six Austen novels: 

``` r

> library(janeaustenr)
> books <- austen_books()
> str(books)
Classes ‘tbl_df’, ‘tbl’ and 'data.frame':       73422 obs. of  2 variables:
$ text: chr  "SENSE AND SENSIBILITY" "" "by Jane Austen" "" ...
$ book: Factor w/ 6 levels "Sense & Sensibility",..: 1 1 1 1 1 1 1 1 1 1 ...
...
> books$text[22225]
[1] "drink to our good journey."

```

The authors' first goal is to put all the books together, one row per
line of a book, with line and chapter number.  Here are a couple of
typical rows in the desired result:

``` r
"children, the old Gentleman's days were comfort… Sense & Sens…    25       1
...
"As we went along, Kitty and I drew up the blind… Pride & Prej…  7398      39
``` 

Here is the solution given by the authors:

``` r
original_books <- austen_books() %>%
   group_by(book) %>%
      mutate(line = row_number(),
         chapter = cumsum(str_detect(text, regex("^chapter [\\divxlc]",
               ignore_case = TRUE)))) %>%
         ungroup()
```


A base-R version within reach of R beginners would begin with **split()**,
to group by books, followed by loop over books.  A more advanced base-R
coder might use FP, first with **lapply()** and then with **Reduce()**
to concatenate the data frames.  

The R beginners version may be unfancy, even old-fashioned, but again
suitable for beginners -- especially from the point of view of
debugging, a key point for noncoder R learners, as noted, and my
main point in this section.   Even the base-R FP version would be quite
debuggable (providing the function called by **lapply()** is named).

By contrast, this example epitomizes the problems with debugging Tidy
code.  Suppose, for instance, that the user had accidentally typed 'sum'
rather than 'cumsum' in the above code.  The output would look like
this:

``` r
> original_books
   text                    book                 line chapter
   <chr>                   <fct>               <int>   <int>
 1 "SENSE AND SENSIBILITY" Sense & Sensibility     1      50
 2 ""                      Sense & Sensibility     2      50
 3 "by Jane Austen"        Sense & Sensibility     3      50
 4 ""                      Sense & Sensibility     4      50
 5 "(1811)"                Sense & Sensibility     5      50
 6 ""                      Sense & Sensibility     6      50
 7 ""                      Sense & Sensibility     7      50
 8 ""                      Sense & Sensibility     8      50
 9 ""                      Sense & Sensibility     9      50
10 "CHAPTER 1"             Sense & Sensibility    10      50
   with 73,412 more rows

```

The 'chapter column' should read 1, not 50.  But there is not error
message, hence no clue as to what the problem might be.

If the code had not used pipes, one could use the R **debug()** or
**browser()** functions, or the RStudio IDE debugging tool.  Even use of
**print()** statements, which I do not recommend in general, would still
be effective of the code had been nonpiped.  (Details below in the
special section on pipes.) But it won't work in the Tidy, i.e. piped,
version.

For instance, consider the code

``` r
debug(group_by)
mtcars %>% group_by(cyl)
```

This produces 

``` r
debugging in: group_by(., cyl)
debug: {
    UseMethod("group_by")
}

```

Dealing with this is far beyond the skillset of R beginners.

Pipes are fundamentally unsuitable for use of debugging
tools, and even just using **print()** statements is impossible. 
 
One partial remedy is the clever **pipecleaner** package for debugging
pipes.  It works only up to a point, and is probably a bit too involved
for R beginners.  Most signifcantly, the package writeup  also notes
that 

> Occasionally it is necessary to restructure code from a piped to an
> unpiped form. 

This makes it clear that pipes (both the Magrittr pipes in Tidy, and
that later native pipes added to base-R), were simply not designed 
with debugging in mind.  As the package author says, sometimes the only
solution is to convert the code to ordinary unpiped form.  (The
package has an aid for this.)

# Should we teach using pipes or functional composition?  Neither!

Pipes play a central role in the Tidy paradigm.  According to the 
Tidy advocates, the claimed alternative--function composition--is
confusing for those without coding background.  That point is debatable,
but once again, the Tidy people are presenting us with a false choice,
pipes or function composition.

There is a "third way"--breaking a sequence of function calls into
separate, intermediate results.  In other words, instead of

``` r
y <- h(g(f(x)))  # functional composition
```

or

``` r
y <- x %>% f %>% g %>% h  # pipes
```

write

``` r
a <- f(x)
b <- g(a)
y <- h(b)
```

The Tidyers do sometimes mention this Third Way, but immediately dismiss
it.  Hadley, for instance, in *R for Data Science* feels that it creates
"cluttered" code.  Well, OK, each person has his/her own aesthetic
values, but really that should pale in comparison to code writability,
readability and debuggability.

For example, consider the Jane Austen novels example above.

``` r
original_books <- austen_books() %>%
   group_by(book) %>%
      mutate(line = row_number(),
         chapter = cumsum(str_detect(text, regex("^chapter [\\divxlc]",
               ignore_case = TRUE)))) %>%
         ungroup()
```

A non-piped version (but still using **dplyr**) would be, say,

``` r
austens <- austen_books() 
booksGrouped <- tibble(group_by(austens,book))
chapterNumbers <- 
   cumsum(str_detect(booksGrouped$text, regex("^chapter [\\divxlc]",
               ignore_case = TRUE)))
mutated <- mutate(booksGrouped,line = row_number(),chapter=chapterNumbers)
original_books <- ungroup(mutated)
```

Now, suppose the user had accidentally typed 'sum' instead of 'cumsum'.
In the unpiped version, the user could run this code one line at a time,
pausing to check the result at each step, either via a debugging tool or
just using **print()**.  She would quickly determine that the line in
which **chapterNumbers** is assigned is the culprit.  This is the
essence of debugging--first narrow down where the error arises.

As noted, one could not do this with the piped version.  Indeed, the
user would likely convert to the non-piped version for debugging!

So why not do this in the first place?  I assert that it would be easier
to write nonpipe code to begin with.  During the writing of the code,
the breaking down the overall action into simple intermediate steps make
it easier for the author to plan out the trajectory of the code.  Each
intermediate step allows the author to "catch one's breath."

For the same reasons, I assert that such code is easier to *write* and
*debug*, but also easier for others to *read*.

Isn't this worth a little bit of clutter?

Even I, with several decades of programming experience in numerous
languages, almost never use functional composition (other than a
nesting depth of 2).  Nor do I use pipes.  I use separate intermediate
statements, as discussed above.  It's just clearer.  And yes, worth the
bit of clutter!

# Other Issues

## ggplot2 versus the Tidyverse

I wrote at the outset of this document that **ggplot2** (GGP2) should
not be considered part of the Tidyverse.  I'll go into detail below, but
first, why does it matter?

The answer is that, among the many people I've interacted with regarding
Tidy, often the first reaaon they cite for liking Tidy is the ease with
which one can code nice graphics.  I fully agree that GGP2 is excellent,
and I use and teach it myself -- but it's not the Tidyverse.  My point,
then, is **they are endorsing Tidy because of something that is not part
of Tidy**.  Indeed, GGP2 is widely used by base-R and Tidy advocates
alike.

RStudio is a business.  Its job, rightly so, is to promote its products.
The GGP2 package had been enormously popular well before Tidy
came along.  Clearly, RStudio saw that, and thus saw that a good way to
sell the Tidyverse was to include the popular GGP2 in the
definition of Tidy.  The message was, "Look how much easier
it is do graphics in Tidy vs. in base-R."

GGP2 does make graphics easier.  But it is misleading to speak of GGP2
as justification for using the Tidyverse, especially in teaching. A
listing of the chronology clarifies the matter:

* The GGP2 package was Hadley Wickham's PhD project, which
  implemented Lee Wilkinson's *grammar of graphics* ideas.  Hadley
  completed his dissertation in 2008, well before Tidy.

* The pre-Tidy nature of GGP2 is exemplified by the fact that in the
  GGP2 code, Hadley has SEVEN instances of calls to **tapply()**--the
  function the Tidiers "love to hate."

* GGP2 uses the '+' operator to modify a plot, rather than the Tidy way,
  which would be to use a pipe.  In fact, Hadley has noted that he would
  use a pipe if he were designing GGP2 today.

Again, GGP2 is a wonderful package.  RStudio has the right to define the
Tidyverse however they feel appropriate.  But RStudio's naming freedom 
does not justify burdening and handicapping R learners with Tidy, 
i.e. FP, **dplyr**, **purrr** and so on.

## Use of functional programming (FP)

If there is one aspect of the Tidy-vs.-base-R debate that in my opinion
demonstrates the problem with Tidy, it's that Tidy advocates want R
beginners to avoid loops.  Indeed, many of those advocates do not even
teach loops at all.

The Tidyers want R beginners to use functional programming (FP) instead
of loops.  But even the Tidyers agree that the concept of functions is
one of the hardest for beginners to learn.  **Thus it makes no sense to
force beginners to use a the tough concept of FP in lieu of the much
more natural loops approach.**  FP does have its place, but it should be
taught as an advanced topic.

An anti-loops mentality has become the Tidy advocates' test of whether
one is a "true believer" in the Tidy philosophy.  I've seen Twitter
posts in which R learners actually apologize for using loops.  

It is worth noting that top university Computer Science Departments have
shifted away from teaching their introductory programming courses using
the FP paradigm, in favor of the more traditional Python, as they deem
FP to be more abstract and challenging.  

An interesting discussion of the topic is in [Charavarty and
Keller](https://www-ps.informatik.uni-kiel.de/~mh/reports/fdpe02/papers/paper15.ps.gz).
Though they support using FP in introductory programming classes for CS
majors,  the authors' goals are antithetical to those of R learners.
The authors list three goals, one of which is to teach theoretical
computer science, certainly not desirable for teaching R in general, let
alone for teaching R to those with no coding experience.  They also
concede that a key concept in FP, *recursion*, is a "signficant
obstacle" even for CS students.  

If FP is tough for CS students, it makes no sense to have nonprogrammer
learners of R use it.

Even Hadley, in *R for Data Science*, says:

> The idea of passing a function to another function is extremely powerful
> idea, and it’s one of the behaviours that makes R a functional
> programming language. It might take you a while to wrap your head around
> the idea, but it’s worth the investment. 

Actually, most non-FP languages allow passing one function to another,
but yes it is a powerful tool, worth the investment of time -- *for the
experienced R programmer*.  But again, it's wrong to force nonprogrammer
learners of R to "wrap their heads around" FP.

And it is much more than just a matter of banning loops.  The '$' and
'[' operators must also be banned, as they allow *side effects*.  In the
example in our Prologue at the top of this essay, the base-R solution

``` r
df[column#,row#] = newvalue
```

causes **df** to change, a side effect.  FP prohibits side effects,
hence the proscribing of '['.  The same problem arises with '$'.

# Where are we now, and where should we be going?

## Tidy as pop culture

Due to a catchy name, a charismatic developer (Hadley), the Bandwagon
Effect, and highly aggressive marketing by a dominant commercial entity,
Tidy now is a major force in the R world.

It has even brought a "pop culture" to R.  One prominent Tidy advocate
(and coauthor of the *Educator Perspective* article) even sells ["Tidy
merchandise"](https://twitter.com/ameliamn/status/1214995483577520131)
-- bags, mugs, and shoes.  A popular Tidy
Tuesday series has arisen on Twitter.  At times, it has even veered into
the realm of cult.  There are many who equate Hadley Wickham with R
itself.  He is treated like a rock star by R "groupies."
What a difference from the staid R community of yore!  We who have been
in R since the early days applaud RStudio for spreading the word,
but it has come at major costs to the well-being of the language.

## Parochialism, polemics snd problems

Putting the hero worship aside, at the very least one can say that many
if not most in that huge Tidy following view R to consist mainly as

   R = dplyr + ggplot2 + RStudio IDE + Rmarkdown

As noted, an article on the teaching of R argues against teaching a mix
of base-R and Tidy to beginners, and RStudio founder JJ Allaire has
refused to recommend teaching a mix.

To us longtime R advocates, this is a tragic irony.  On the one hand,
again RStudio is to be congratulated for greatly increasing the worldwide
count of R users.  But the tragedy is that those users tend to be
ill-equipped to actually *use* R productively, compared to "graduates"
of standard base-R courses -- and *without* Tidy being easier to learn.

The danger of being wrapped up in hoopla and crusade, of course, is that one can
lose sight of reality.  In my view, this is what has happened with Tidy.

Equally important is the impact on the R language itself.  In his
aforementioned keynote address, Prof. Peng asked,

> It will be interesting to see how things evolve, and whether the
> community can sustain multiple ways of programming.  I think that it
> can, but that's my opinion.

I am indeed worried that R will split into two different "dialects.
Though Peng's speculation may be correct if one views R strictly as a
programming language, R is a *statistical tool*.  As explained
earlier in this document, Tidy is at odds with the most R statistical
packages.  Though packages like **broom** might be developed to bridge
the gap in some specific instances, there obviously are far too many
packages for this to be realistic.  It is here that the divide between
the Tidy and base-R worlds may be mostly keenly manifest.

Sadly, that divide has occasionally become personal.  For instance,
there was harsh public criticism from some in RStudio and the firm's
allies, toward the base-R-favoring R/Finance Conference in 2018, accusing the
conference organizers of being insensitive to gender diversity.  In my
view, this was quite
[unfair](https://matloff.wordpress.com/2019/05/18/r-finance-1-year-later/),
and it was my first exposure to a bitter base/Tidy divide.  It was also
my first real exposure to Twitter.  Shortly after the conference, an
RStudio employee asked me, "What do you think of the tweetstorm about
the conference?", total news to me.  I was shocked by the vitriol.

Some in RStudio have Twitter-blocked some of the Tidy critics, abruptly
ending frank but civil conversation.  In my case, one major RStudio
developer [made quite a show of
it](https://twitter.com/romain_francois/status/1140860812837445632?s=19),
tweeting a screen shot in which "You have blocked this user" is repeated
dozens of times.  There was also tension between RStudio and Matt Dowle,
author of **data.table**, a technically superior competitor to
**dplyr**.

## Some room for optimism

But the good news is that both sides have been making attempts at
reconciliation.  Especially notable is that the R Core Group, a body
that controls the development of base-R, recently added a native pipe to
the language.  I doubt many in that group actually use it, but it is an
impressive olive branch.  The R Foundation now includes a number of
pro-Tidy members.

RStudio, including Hadley, has also made various conciliatory public
remarks.  Indeed, my meeting with RStudio CEO JJ Allaire in 2019 came at
JJ's suggestion.  Around that time, JJ also met with Matt Dowle.  Also
in 2019, RStudio stopped viewing **data.table** as a rival, and
announced the release of **dtplyr**, a Tidy-syntax front end to
**dplyr**.  Since **data.table** is much faster on large datasets than
**dplyr**, this was a win-win for the entire R community.

Hopefully we will be seeing more of these positive trends in the coming
years.  As I explained in that meeting with JJ, the best form of
reconciliation on RStudio's part would be to encourage instructors in
the Tidy community to teach a mixture of Tidy and base-R.  

It should be noncontroversial that R learners should be given a choice
of tools, and that they themselves should decide what is the best one to
use in any given setting.  And if for example some thus-empowered useR
feels that

``` r
mtcars$hwratio <- mtcars$hp / mtcars$wt
```

is more convenient than

``` r
mtcars %>% mutate(hwratio=hp/wt) -> mtcars
```

so be it.  There will be other cases in which the graduates of mixed
instruction find the Tidy solution more appealing.  Rest assured, Tidy
is here to stay.

## RStudio, as a Public Benefit Corporation, holds the key

One very important event is that RStudio changed status to a Public
Benefit Corporation (PBC), which it
[announced](https://www.rstudio.com/blog/rstudio-pbc/) in 2019.  

In my opinion, in spite of various actions the firm might point to that
are aimed at the public good, **RStudio has not lived up to its status as
a PBC.**

I was shocked to find in 2022 how expensive the RStudio conference is,
reportedly [US
$1500](https://twitter.com/fishiintheC/status/1553001832166969344).
Though there were probably some registration types that are cheaper than
this, this fee is exhorbitant.  RStudio is a commercial entity, and the
conference promotes its product. Given this status, I had assumed the
conference would be free, maybe a small nominal fee. As a PBC, RStudio
is legally committed to the public good.  Instead, the fee more evokes
"Charge what the traffic will bear" than "public good."

And as a PBC, and as a commercial entity that dominates a pre-existing
open source product, RStudio should take a good, hard, dispassionate
look at what is best for R learners.  The firm should move beyond using
misleading testimonials to rationalize its rigid stance.

I thus renew the suggestion I made to JJ in 2019, and **ask that
RStudio recommend to the Tidy teaching community that they teach a
mixture of Tidy and base-R.**  The firm's transtioning to a broader,
less R-focused copy under the name Posit makes this even more important.


