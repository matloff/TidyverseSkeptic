# Teaching R in a Kinder, Gentler Manner: Use Base-R, Not the Tidyverse  

## Author:  Prof. Norm Matloff, University of California, Davis

I teach in the Computer Science Dept. at UC Davis, where I formerly was
Professor of Statistics. I am an award-winning textbook author, 
and am also the recipient of university awards for teaching
and public service. 

Specifically in terms of R, I have been an R user and developer since
near the beginning, having used R's predecessor S before that.  I've
published several books that use R, and have served as the
Editor-in-Chief of the *R Journal*. My R tutorial for beginners,
[fasteR](https://github.com/matloff/fasteR), has become my most popular
GitHub repo, with over 300 GitHub stars.

But it goes far beyond that; I really am intensely interested in how
people learn, from children to middle-aged adults. Among other things,
I've taught English As a Second Language, and have taught a short course
on probability to sixth-graders.

See my [full bio](https://heather.cs.ucdavis.edu/matloff.html)

# Note on ggplot2

Though RStudio presents **ggplot2** as part of the Tidyverse, it
predates Tidy and does not use the Tidy paradigm.  In my discussion
here, my references to Tidy do not include **ggplot2**, a package of
which I am an enthusiastic user and teacher.  More details later in this
document.
[link to GGPs](#other-issues)


# Kudos to RStudio, But with a Wrong Turn

I like and admire the RStudio people, including the Tidyverse
originator, Hadley Wickham, and have always supported them, both
privately and
[publicly](https://matloff.wordpress.com/2018/02/22/xie-yihui-r-superstar-and-mensch/).
They and I have been interacting from the beginning, when the firm
consisted of only founder JJ Allaire and ace developer Joe Cheng.  I
highly praise the firm to my students, and I use and recommend 
Hadley's (non-Tidyverse) packages **ggplot2** and **stringr**, and 
on occasion **devtools** has been an absolute lifesaver for me.
Hadley was the internal reviewer for my book, *The Art of R
Programming*, and I was one of the internal reviewers for Hadley's
*Advanced R* (2nd. ed.).

Nevertheless, I believe that **RStudio took a wrong turn when it decided
to promote the Tidyverse** for beginning learners who have no prior
coding background.  Tidy makes it more difficult for noncoders to learn
R, and leaves them less able to productively.


# Teachability overview

* Again, my focus here is on teaching R to those with little or no
coding background.  I am *not* discussing teaching Computer Science
students. 

* Tidy is concise, but that conciseness is often far too abstract for beginners.
The Tidyers confuse *concise* code with *easily
writeable/readable/debuggable/teachable* code.  The 
former does not imply the latter, and more often implies 
the opposite.

* Tidy's abstractness is due to philosophy of functional programming
(FP). The latter is popular with many sophisticated computer
scientists, but is difficult even for computer science students, thus
unsuited for nonprogrammer students of R.  (Actually, base-R has a rich
set of its own FP functions, but my point is that these are not
appropriate at the start of the R learning process.)

* The FP philosophy replaces straightforward loops with abstract use of
functions. Since functions are the most difficult aspect for noncoder
R learners, FP is clearly not the right path for such learners.

* A major problem with Tidy for R beginners is cognitive overload: The
basic operations contain myriad variants. Though of course one need
not learn them all, one needs some variants even for simple operations,
e.g. pipes on functions of more than one argument.

* Indeed, even many Tidy advocates concede that it is in various senses
often more difficult to write Tidy code than base-R. Hadley says, for
instance, "it may take a while to wrap your head around [FP]."

* Using Tidy to teach R results in it taking *more* time to learn *less*.
The students learn a few **dplyr** verbs well, but that equips them to
do much less with R than a standard R beginners course would teach.
That leaves the learners less equipped to put R to real use, compared to
"graduates" of standard base-R courses.

* Once one goes beyond the simple **mutate/select/filter/summarize**
level, Tidy programming can be of low readability.

* Tidy advocates also concede that debugging Tidy code is difficult,
especially in the case of pipes. Yet noncoder learners are the ones
who make the most mistakes, so it makes no sense to have them use a
coding style that makes it difficult to track down their errors.

* The obsession among many Tidyers that one must avoid writing loops,
the '$' operator, brackets and so on often results in obfuscated
code.

* The refusal to teach '$' and the de-emphasis on, or even complete lack of
coverage of, R vectors is a major handicap for Tidy "graduates" to
making use of most of R's statistical functions and statistical packages.  

* Note once again, that in discussing teaching, I am taking the target
audience here to be **nonprogrammers** who wish to use R for data
analysis.  Eventually, they may wish to make use of FP, but at the
crucial beginning stage, keep it simple, little or no fancy stuff.

# Using Tidy Hinders the Learning Process:  Case Studies 

## Case study: delayed learning (I)

Let's look at  my online R tutorial,
[**fasteR**](http://github.com/matloff/fasteR)).  Consider, for
instance, an innocuous line like 

``` r
> hist(Nile)
```

i.e. drawing a simple histogram of R's built-in Nile River dataset.  

This is in the very first lesson in my tutorial.  Easy!  By contrast,
the Tidy crowd forbids use of base-R plots, insisting on using
**ggplot2**.  I also prefer **ggplot2** to base-R graphics (though as
explained below, it should not be considered part of the Tidyverse), but
here we have a much more important goal--to give students an actual
useful application of R right from the start.

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

Also in my very first lesson, I do

``` r
> mean(Nile[80:100])
```

printing the mean Nile River flow during a certain range of years.
Incredibly, not only would this NOT be in a first lesson with Tidy, the
students in a Tidy course may actually *never* learn how to do this.
Typical Tidiers don't consider vectors very important for learners, let
alone vector subscipts. 

As a concrete example of this Tidy point of view, consider the book
*Getting Started with R*, by Beckerman *et al*, Oxford University Press,
second edition, 2017.  The book makes a point of being 
["Tidyverse compliant"](https://twitter.com/GSwithR/status/996830294367002625).
In 231 pages, vectors are mentioned just briefly, with no coverage of 
subscripts.

In other words, **even after one lesson, the base-R learner would be way
ahead of her Tidy counterparts.**

## Case study: delayed learning (II)

A researcher tweeted in December 2019 that an introductory statistics
book by Peter Dalgaard is "now obsolete," because it uses base-R rather
than Tidy.  Think of what an update to Tidy would involve, how much extra
complexity it would impose on the students.  Here is an early lesson from the
book:

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

## Case study:  tapply() (I)

One of the most commonly-used functions in base-R is **tapply()**.  It's
quite easy to teach beginners, by presenting its call form to them:

``` r
tapply(what to split, how to split it, what to apply to the resulting chunks)
```

However, for some reason Tidy advocates deeply hate this function.
Indeed, for many of them, **tapply()** epitomizes what's wrong with
base-R.  

Indeed, when the Tidyverse was first developed, Prof. Rogern Peng gave a
keynote talk, *Teaching R to New Users--from tapply to the Tidyverse*,
also presented as [a Web
page](https://simplystatistics.org/posts/2018-07-12-use-r-keynote-2018/).
Actually, **tapply()** is not mentioned in Dr. Peng's talk or in the
printed version, but the title says it all:  One should teach Tidy, not
**tapply()**.

Surprisingly, though, in making his comparison of Tidy to base-R, his
base-R example is **aggregate()**, not **tapply()**.  The complexity of
**aggregate()** function makes for an unfair comparison, as **tapply()**
is much simpler, and perfect for R beginners.  

Here is an example from the Peng talk, using the built-in R dataset
**airquality**:

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
tapply(airquality$Ozone,airquality$Month,function(x) mean(x,na.rm=T))
```

Both the Tidy and **tapply()** code are simple.  Both are easily grasped
by beginners. After being presented with some examples, beginners have
no trouble using either of them in a new setting of similar type.  The
Tidy version requires two function calls rather than one for base-R.
But again, both versions are simple, so let's call it a tie.  But is it
certainly not the case that the Tidy version is *easier* to learn.

## Case study:  Tidy's banning the $ sign and brackets

Tidyers believe that two of the most basic operations in R, the \$ sign
and bracketing, are harmful.  For instance, consider an example in
[an article by Tidy advocates](https://arxiv.org/abs/2108.03510)
by Tidy advocates, *An Educator's Perspective of the Tidyverse.* 

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

```

As noted earlier, one should not conflate conciseness with clarity.  But
here the base-R code is both more concise *and* more straightforward.
The Tidyers might even agree, except that the code uses '$'.  As the
article puts it:

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
advance warning.

As to brackets, Tidy essentially ignores vectors.  Consider the
following base-R coe:

``` r
x <- c(5,12,13,1)
   x[x > 8]
```

Probably the simplest way to do this in Tidy would be:

``` r
data.frame(x=x) %>% filter(x > 8)
```

That's a lot of machinery to implement one little vector operation, one
that is of course quite common.

## Case study:  an overly rigid philosophy

It is disappointing that the Tidyers wish to replace base-R, rather than
supplement it.  

One of the most troubling aspects of the Tidy movement is their rigidity
and insistence on "loyalty."  For instance, the above-cited *Educator's
Perspective* article

> ...one thing we have learned is that when we teach the tidyverse
> consistently, the presence of base R patterns (e.g., using square
> brackets to select columns instead of dplyr::select()) stands out.  An
> assignment completed entirely with base R syntax (in a class where
> tidyverse is being used) could signal a student who is less engaged with
> the overall learning materials for the course.  

Consider the following simple example:  Say we wish to add to the
**mtcars** data a column consisting of the horsepower-to-weight ratio.

In base-R, it is extremely simple:

``` r
   mtcars$hwratio <- mtcars$hp / mtcars$wt
```

Want to add a column to a data frame?  Hey, just add it!

But in Tidy:

``` r
   mtcars %>% mutate(hwratio=hp/wt) -> mtcars
```

Still not terribly complex, but we're invoking some machinery -- piping,
a function call, and reassigning to the original data frame.

Why would we deprive R learners of very simple, direct and effective
tools like this?  Just for the sake of Tidy "purity," implicit in the above
quoted passage?

Students who are taught the Tidy version of the above and then are shown
the base-R one will say, "Wow!  That's much easier.  Thanks for the
shortcut."  And I can guarantee, a few would say, "Why didn't you tell
us this way in the first place?"

This brings me to my next point.

The "naughty kids" aspect in the above quote,

> An assignment completed entirely with base R syntax (in a class where
> tidyverse is being used) could signal a student who is less engaged with
> the overall learning materials for the course.

sounds a bit authoritarian, and I've seen consequences.  For instance,
one R learner proudly displayed on Twitter some code she had managed to
write, but she guiltily apologized for using a loop.

What is also intriguing about the above quote on "naughty kids" is its
seeming implication that such a student's use of base-R would be "taking
the easy way out." But doesn't that mean base-R is easier?

Finally, regarding the "purity" view in the article, advocating mixing
Tidy and base-R in teaching, I did suggest that to RStudio founder and
head JJ Allaire, but he did not like the idea either.

## Case study:  Tidy as an obstacle to R statistical methods

   In the last section, we discussed the Tidyers' opposition to the '$' and
   brackets operations.  This is an obvious impediment to R's statistical
   operations. 

   Statistics in R is mainly are vector- and matrix-oriented.  (A matrix 
         is a special case of a vector.)  Thus we immediately see a problem with
   Tidy.

   Equally important, most of the R statistical functions return S3 object,
   i.e. lists, accessible via '$'.  I would find it difficult to teach a
   course in linear regression, principal components, log-linear models and
   so on to students who did not have solid prior experience with '$'.

   [Here](https://clauswilke.com/blog/2020/09/07/pca-tidyverse-style/) is
   an example of bridging the gap between Tidy and statistics, by Claus
   Wilke, who begins by reporting, "I’ve finally figured out how to perform a PCA using the tidyverse."  The answer is to use the **broom** package.

   As it was, even that package did not quite work, he said, though the
   development version did.  And what about the thousands of CRAN packages
   that return S3 objects?  Is **broom** going to provide a Tidy interface
   to each one?  That of course would be unrealistic.

   A fundamental problem, from my point of view, is that the RStudio people
   are not primarily statisticians.  Their focus is on developing software,
   primarily for data wrangling and graphics.  They do this quite well, but
   they are not the types who sit around debating, for example, the
   propriety of p-values.  Statistics is not foremost on their radar
   screens, and this sad gap between Tidy and statistics is a result.


## Case study:  tapply() (II)

   Besides *learnability*, another goal for noncoder R learners is
   *usability.*  In this light, it's instructive to look at what happens
   when in the built-in **mtcars** dataset one groups by two aspects,
   **cyl** and **gear**, rather than just say **cyl**:

``` r
   > mtcars %>%
   group_by(cyl,gear) %>%
summarize(mean(mpg))
# A tibble: 8 x 3
# Groups:   cyl [3]
   cyl  gear `mean(mpg)`
   <dbl> <dbl>       <dbl>
   1     4     3        21.5
   2     4     4        26.9
   3     4     5        28.2
   4     6     3        19.8
   5     6     4        19.8
   6     6     5        19.7
   7     8     3        15.0
   8     8     5        15.4
```

   Compare to base-R:

``` r
> tapply(mtcars$mpg,list(mtcars$cyl,mtcars$gear),mean)
   3      4    5
   4 21.50 26.925 28.2
   6 19.75 19.750 19.7
   8 15.05     NA 15.4
```

   With **tapply()**, students do have to be told that in the case of more
   than one grouping variable, they need to surround the variables with
   'list'.  Again, once they are given examples, students have no trouble
   with this.

   But look at the form of the output:  The Tidy version outputs a tibble,
   rather hard to read, while **tapply()** outputs an R matrix, printed out
   as a two-way table.  The latter form is exactly what many students need
   in their applications, e.g.  social science research.  

   In searching through the hundreds of functions in **dplyr**, it is not
   clear to me which one, if any, can convert that Tidy output to the very
   informative tabular view that **tapply()** provides.  If there is one,
   the fact that one is not easily identifiable illustrates my point above
   that Tidy is actually very bloated, not suitable for beginners.

   Moreover, the **tapply()** output is more informative in a second sense,
   letting the user know that there were no 8-cyliner, 4-speed cars, again
   the kind of thing that is quite meaningful in many applications.  

   Actually, the Tidy version can be modified in order to notice that empty
   group.  Then things get really bad for Tidy:

``` r
   > mtcars$cyl <- as.factor(mtcars$cyl)
> mtcars$gear <- as.factor(mtcars$gear)
   > mtcars %>% 
   group_by(cyl,gear,.drop=FALSE) %>% 
summarize(mean(mpg))
# A tibble: 9 x 3
# Groups:   cyl [3]
   cyl   gear  `mean(mpg)`
   <fct> <fct>       <dbl>
   1 4     3            21.5
   2 4     4            26.9
   3 4     5            28.2
   4 6     3            19.8
   5 6     4            19.8
   6 6     5            19.7
   7 8     3            15.0
   8 8     4           NaN  
   9 8     5            15.4
```

   There's trouble for R beginners right away, in the need to convert to
   factors, something not mentioned in the Tidy documentation, and which
   would further complicate things for R beginners even if it were
   documented.  Furthermore, the instructor would need to explain the
   **drop=FALSE**

   This illustrates why one Tidy advocate dismissed my example of grouping
   by two factors as "advanced," not suitable for a discussion of how R
   beginners learn.  It IS advanced for Tidy learners.  But it's clear that
   for base-R learners, it's not advanced at all.  Indeed, examples like
   this are standard fare in base-R courses.

   I'd give base-R the clear win for teaching purposes here. 

## Case study:  Tidy obstacles to debugging

Here is an example from *Text Mining with R*, by Julia
Silge of RStudio, and David Robinson. It's a great introduction to the
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
code.  It is impossible to effectively use the R **debug()** or
**browser()** functions, let alone the RStudio IDE debugging tool, on
the code as is.  There are two major obstacles, both fundamental to 
Tidy in general:

* Use of R generic functions.  For instance, consider the code

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

* Use of pipes.

Pipes are fundamentally unsuitable for use of debugging
tools, and even just using **print()** statements is impossible. 
 
One partial remedy is the clever **pipecleaner** package for debugging
pipes.  It works only up to a point, and is probably a bit too involved
for R beginners.  Most signifcantly, the package writeup  also notes
that 

> Occasionally it is necessary to restructure code from a piped to an
> unpiped form. 

This makes it clear that pipes were simply not designed 
with debugging in mind.  As the package author says, sometimes the only
solution is to convert the code to ordinary unpiped form.  (The
package has an aid for this.)

## Case study:  poor readability, unreasonable cognitive overload

As noted, R courses using the Tidyverse often do rather little beyond
their canonical *data %>% group_by %>% mutate %>% summarize* paradigm.
That leaves the learners less equipped to put R to real use, compared to
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

# output
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
fact that **summary()** yields an S3 object with component **r.squared**.  
Yes, sometimes it is helpful to hide the details, but
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

Granted, loops can use their clarity if they are nested.  This can be
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
   # the work of what would have been the inner loop goes here
}
```

rather than say, one of the **apply()** or **purrr** functions.

**Again, there is a serious problem of cognitive overload.** Tidyverse
students are being asked to learn a much larger volume of material,
which is clearly bad pedagogy.  See ["The Tidyverse
Curse"](https://www.r-bloggers.com/the-tidyverse-curse), in which the
author says *inter alia* that he uses "only" 60 Tidyverse functions --
60!  The "star" of the Tidyverse, **dplyr**, consists of 263 functions. 

While a user initially need not use more than a small fraction of those
263 functions, the high complexity is clear.  Every time a user needs some
variant of an operation, she must sift through those hundreds of
functions for one suited to her current need.  

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
 
By contrast, if the user knows base-R (not difficult), she can handle
any situation with just a few simple operations.  The old adage applies:
"Give a man a fish, and he can eat for a day. Teach him how to fish, and
he can eat for a lifetime."  




# Other Issues

## ggplot2 vs. the Tidyverse

I wrote at the outset of this document that **ggplot2** (GGP2) should
not be considered part of the Tidyverse.  I'll go into detail below, but
first, why does it matter?

The answer is that, among the many people I've interacted with regarding
Tidy, often the first reaaon they cite for liking Tidy is the ease with
which one can code nice graphics.  I fully agree that GGP2 is excellent,
and I use and teach it myself -- but it's not the Tidyverse.  My point,
then, is they are endorsing Tidy because of something that is not part
of idy.

RStudio is a business.  Its job, rightly so, is to promote its product,
which in a broad sense is R.  All of RStudio's revenue comes from
services involving R, and the more R users there are, the better for
RStudio.  (And by the way, also the better for us longtime R advocates;
RStudio has done a superb job of expanding the number of R users.)

RStudio genuinely believed that Tidy would facilitate the usage of R.
The GGP2 package had been enormously popular well before Tidy
came along.  Clearly, RStudio saw that, and thus saw that a good way to
sell the Tidyverse was to include the popular GGP2 in the
definition of Tidy.

That of course is fine, but it is misleading to speak of GGP2
as justification for using, especially teaching, the Tidyverse.  A
listing of the chronology clarifies the matter:

* The GGP2 package was Hadley Wickham's PhD project, which
  implemented Lee Wilkinson's *grammar of graphics* ideas.  Hadley
  completed his dissertation in 2008, well before Tidy.

* Hadley introduced the Tidy concept in his
  [2014 paper](https://www.jstatsoft.org/v59/i10/paper):  Each variable
  forms a column, each observation forms a row (EVCEOR).  Of course, there
  was nothing new here, as most of base-R assumes EVCEOR format.  Indeed, 
  Hadley put the base-R workhorse function, **plot()**, on an equal
  footing with GGP2:

    > Most graphical tools in R are input-tidy, including the base plot()
    > function, the lattice family of plots (Sarkar 2008) and ggplot2 (Wickham
    > 2009).

* As Hadley's packages (and RStudio) gained popularity, the term 
  *Hadleyverse* became used to describe his collection of projects.  He
  demurred, though, and suggested the term *Tidyverse* in his 
  2016 useR! conference keynote.

* Even the Tidy advocacy article cited earlier, *An Educator's
  Perspective*, notes that GGP2 was only brought under the Tidy
  "umbrella" later on:

    > Many of the core packages in the tidyverse were originally developed
    > independently to address specific phases of the data science cycle, and
    > subsequently came together under the tidyverse umbrella in 2016
    > (Smith 2016)...

  (The Smith citation lists GGP2 and **purrr**.)

* As noted above, there is nothing especially "Tidy-ish" about GGP2.  
  It is no more EVCEOR-ish than the base-R **plot()** (and most of
  base-R).  It does not use pipes.  (Hadley has said if he designed 
  GGP2 today, he would base it on pipes.)  It does not use FP.
  
Again, GGP2 is a wonderful package.  RStudio has the right to define the
Tidyverse however they feel appropriate.  (It was originally called the
Hadleyverse, as it was a collection of Hadley's software projects, but
he demurred.) But RStudio's naming freedom does not justify burdening R
learners with Tidy, i.e. FP, **dplyr**, **purrr** and so on.

## Tidyverse "testimonials"

There has been no study of Tidy advocates' teachability claim, and
indeed designing a proper "randomized clinical trials" study would be
very difficult if not impossible.  (My arguments in this document merely
appeal to common sense, again no data.)  But many Tidy teachers report
great success with the approach.

One major issue with this "success" (aside from the improper conflation
of Tidy with GGP2) is that Tidy R courses are scaled down in scope,
compared to the base-R ones.  A typical Tidy R course does not equip
students to do much in R (whether, base or Tidy). They teach a few **dplyr**
verbs, a few GGP2 calls, and provide examples that the students can
mimic. Much time is spent on the RS IDE and R Markdown. Students emerge
with a false sense of empowerment.  Teacher and students alike are
happy, but misleadingly so. 


## Use of functional programming

If there is one aspect of the Tidy-vs.-base-R debate that in my
opinion demonstrates the problem with Tidy, it's that
Tidy advocates want R beginners to avoid loops.  Indeed, those
advocates may not even teach loops at all in a basic course.

The Tidiers want R beginners to use functional programming (FP) instead
of loops.  But even they agree that the concept of functions is one of
the hardest for beginners to learn.  **Thus it makes no sense to force
beginners to use a the tough concept of FP in lieu of the much more
natural loops approach.**  FP does have its place, but it should be
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


