# TidyverseSkeptic
Teach R in a kinder, gentler--and more productive--manner: Use base-R rather than the Tidyverse.

## Dr. Norm Matloff, University of California, Davis

# Bio
I teach in the Computer Science Dept. at UC Davis, where I formerly was Professor of Statistics. I am an award-winning textbook author, teacher and public servant. See his[full bio](https://heather.cs.ucdavis.edu/matloff.html)

Specifically in terms of R, I have been an R user and developer since near the 
beginning, having used R's predecessor S before that.  I've 
published several books that use R, and have served as the 
Editor-in-Chief of the *R Journal*.


# Disclaimer

This essay is somewhat frank, involving the very popular Tidyverse and
RStudio. I hope it is polite and taken as constructive criticism.  

I like and admire the RStudio people, including the Tidyverse
originator, Hadley Wickham, and have always supported them, both
privately and
[publicly](https://matloff.wordpress.com/2018/02/22/xie-yihui-r-superstar-and-mensch/).
They and I have been interacting from the beginning, when the firm
consisted of only founder JJ Allaire and ace developer Joe Cheng.  I
highly praise the firm to my students, and I use and recommend 
Hadley's (non-Tidyverse) packages **ggplot2** and **stringr**, and 
on occasion **devtools** has been an absolute lifesaver for me.

Nevertheless, I believe that **RStudio took a wrong turn when it decided to promote the Tidyverse** for beginning learners who have no prior coding background.


## TEACHABILITY OVERVIEW

* My biggest concern is involves teaching of R.  **Tidy makes it more
  DIFFICULT for nonprogrammer learners of R to become proficient in the
language**.

* The Tidyverse arose from the desire to have a set of functions/packages that
   are consistent with each other, a "purist" philosophy that appeals,
for instance, to computer scientists.  The Tidyverse also borrows from
other "purist" computer science (CS) philosophies, notably *functional
programming* (FP).  The latter is abstract and theoretical,
DIFFICULT EVEN FOR CS STUDENTS, and thus it is clear that **Tidy 
is an unwise approach for nonprogrammer students of R.**

*  In other words, the **Tidyverse is general is far too complex for learners
    without prior coding background**, causing what psychologists call
<i>cognitive overload</i>.

*  Indeed, even many Tidy advocates concede that it is in various
    senses often more difficult to write Tidy code than base-R.  Hadley 
    says, for instance, "it may take a while to wrap your head around [FP]."

* RStudio has done an admirable job in bringing more women and
  underrepresented minorities into R.  Yet by saddling them with the
  complicated Tidyverse system, RStudio has made it more difficult for
  these groups to make contributions to the language, in the form of
  writing CRAN packages, authoring books and so on, which require good
  facility with base-R even if the code is largely Tidyverse.  This of
  course is equally true for anyone, not just those in these groups, but
  it's sad that RStudio is hurting the very people it wants to help.

# <a name="teachable"> </a> TEACHABILITY

Teaching has been a keen interest of mine since my college days.  I've
been a teacher of stat and computers for many years, and have won
various teaching awards.  My textbook, *Statistical Regression and
Classification: from Linear Models to Machine Learning*, was the
recipient of the 2017 Ziegel Award.
 
But it goes far beyond that; I really am intensely interested in how
people learn, from children to middle-aged adults.  Among other things,
I've taught English As a Second Language to immigrant adults, most of
whom have had less than a high school education.

In discussing teaching, I am taking the target audience here to be
**nonprogrammers who wish to use R for data analysis**, not those who wish
to become professional R programmers.

### Case Study: Teaching One's First Lesson in R

The Tidyverse is just too complex for beginners.  Here some quick
examples of the complexity of Tidy, and its consequent unsuitability for
use in teaching nonprogrammer learners of R.

Let's look at  my online R tutorial,
[**fasteR**](http://github.com/matloff/fasteR)).  Consider, for
instance, an innocuous line like 

``` r
> hist(Nile)
```

i.e. drawing a simple histogram of R's built-in Nile River dataset.  

This is in the very first lesson in my tutorial.  Easy!  By contrast,
the Tidy crowd forbids use of base-R plots, insisting on using
**ggplot2** (which again is not Tidy, but is considered as such by the
Tidy advocates).  To be Tidy the instructor would have to do something
like

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

### Case Study: Dalgaard book

A researcher tweeted in December 2019 that an introductory statistics
book by Peter Dalgaard is "now obsolete," because it uses base-R rather
than Tidy.  Think of what an update to Tidy would involve, how much extra
complexity it would impose on the students.  Here is an example from the
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

### The Tidyverse advocates' claims

As a lifelong passionate teacher, I strongly question the claim made by
Tidyverse advocates that it facilitates the teaching of R to
non-programmers, as opposed to teaching them base-R.  

There has been no study of Tidy advocates' teachability claim.
Advocates often provide testimonials from students like 

* "I learned R using Tidyverse, and now am productive in R" 

* "I like the English-like nature of the Tidyverse"

* "I can make beautiful graphics with the Tidyverse"

* "Tidyverse showed me the fluidity of data"

Advocates who are instructors will echo those statements, and add, e.g.

* "Base-R is good for professional programmers, but the Tidyverse is the
  best R learning tool for non-techies who just want to do data
analysis"

* "R was created by statisticians, for statisticians.  But we are data
  scientists, mainly interested in producing graphs and tables"

* "The Tidyverse is **modern** R, for the rest of us"

All of these statements are either misleading, irrelevant to the
teachability issue, or downright meaningless.  They say nothing at all
about the teachability of base-R in comparison to Tidy.  (It is ironic
that advocates who present such statements are data scientists, who
ought to know the need for a control group.)

### Tidyverse makes learning harder, due to adding much complexity 

Contrary to the Tidy advocates' claim, I believe using the Tidyverse
makes things more *difficult* for learners without prior programming
background.  

**There is a serious problem of cognitive overload.** Tidyverse students
are being asked to learn a much larger volume of material, which is
clearly bad pedagogy.  See ["The Tidyverse
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

### What Tidy promoters want R beginners NOT to learn

The Tidyers make a point of avoiding the most basic parts of base-R:

* the '$' operator

* '[[ ]]'

* loops

* **plot()** and the associated basic graphics functions

They would argue that this "simplifies" the learning process, but
actually it forces beginners to come up with more complex, less
intuitive and harder-to-read solutions.

### Case Study: the tapply() Function

One of the most commonly-used functions in base-R is **tapply()**.  As
noted below, for some reason Tidy advocates deeply hate this function. 
Indeed, for many of them, **tapply()** epitomizes what's wrong with base-R.
But it is perfect for R beginners.  

Consider a common example in tutorials on the Tidyverse, involving R's
**mtcars** dataset.  The goal is to find mean miles per gallon, grouped
by number of cylinders.  The Tidy code offered is

``` r
mtcars %>%
   group_by(cyl) %>% 
   summarize(mean(mpg))
```

Here is the base-R version:

``` r
tapply(mtcars$mpg,mtcars$cyl,mean)
```

Both are simple.  Both are easily grasped by beginners. After being
presented with some examples, beginners have no trouble using either of
them in a new setting of similar type.  The Tidy version requires two
function calls rather than one for base-R.  But again, both versions are
simple, so let's call it a tie.  But is it certainly not the case that
the Tidy version is *easier* to learn.

Again, so far, a tie.  But it's instructive to look at what happens when
one groups by two aspects, **cyl** and **gear**, rather than just
**cyl** as above.:

``` r
> mtcars %>%
+ group_by(cyl,gear) %>%
+ summarize(mean(mpg))
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
+    group_by(cyl,gear,.drop=FALSE) %>% 
+    summarize(mean(mpg))
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
documented.

This illustrates why one Tidy advocate dismissed my example of grouping
by two factors as "advanced," not suitable for a discussion of how R
beginners learn.  It IS advanced for Tidy learners.  But it's clear that
for base-R learners, it's not advanced at all.  Indeed, examples like
this are standard fare in base-R courses.

I'd give base-R the clear win for teaching purposes here. 

### Use of functional programming

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
posts in which R learners actually apologize for using loops.  And in
[another tweet](https://twitter.com/cynthiahqy/status/1444871989152280578),
the author proudly cites the loop-free nature of her code, but her
wording shows (rightly) that this was difficult to achieve:

> Excited and a bit nervous to share some initial work on a #tidyverse
> inspired #rstats 📦 for wrangling data from different classifications
> (e.g. trade/labour) into consistent panels WITHOUT FOR-LOOPS

The author does claim that the FP format is clearer for data wrangling.
That's debatable -- the proper remedy is always to put an outline of
one's code in comment lines -- but at the very least, this again shows that
**FP makes the learning process harder for beginners.**

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

### purrr vs. base-R example 

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
  particular example, and a dozen others for even basic use. This is an
excellent example of Tidy's cognitive overload problem.  Actually,
the Tidyverse FP package, **purrr**, has 52 different map functions!  
(See below.)

* The first '~' in that first map call is highly nonintuitive.  Even
  experienced programmers would not be able to guess what it does. This
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


### Tibbles

Similarly, it is bad pedagogy to force students to learn tibbles, a more
complex technology, instead of data frames, a simpler one.  The types of
"nonorthogonal" situations that tibbles are meant to address should be
an advanced topic, not for beginners with no coding background.

Those advanced situations involve data frames in which row/column
elements are not *atomic* objects, i.e. not simple numbers, character
strings or logical values.  **This is a "straw man" set up by the Tidy
advocates'**; R beginners are very unlikely to encounter data frames of
this type.  Indeed, most if not all R textbooks do not even have
examples of this kind of data.

### The English issue

Again, the point most emphasized by Tidyverse advocates is that the
Tidyverse is more teachable because of its "English-like" syntax. 

Below is a comparison of the "English" **dplyr** to the "non-English"
**data.table** (adapted from
[here](https://atrebas.github.io/post/2019-03-03-datatable-dplyr/)):
We'll again use R's built-in **mtcars** dataset.

``` r 
mtdt <- as.data.table(mtcars);  mtdt[cyl == 6]  # data.table syntax
mttb <- as_tibble(mtcars);  filter(mttb,cyl == 6)  # dplyr syntax 
``` 

Is there really any difference?  Can't beginners, even without
programming background, quickly adapt to either one after seeing a few
examples?  Even those who claim high teachability for **dplyr** do
readily agree that their students could also easily pick up
**data.table**, or for that matter my preference for beginners, base-R,
given some examples.

We saw earlier that the **purrr** example,

``` r
mtcars %>%
  split(.$cyl) %>%
  map(~ lm(mpg ~ wt, data = .)) %>%
  map(summary) %>%
  map_dbl("r.squared")
```

would be baffling even to experienced (but non-R) programmers, starkly
contradicting the claimed "English-like clarity" of Tidy.  And the
**dplyr** meaning of **mutate** is nowhere near its English meaning, and
again, would not be guessed even by a non-R professional programmer.

In other words, though students may say they like the "English" aspect
of Tidy, the benefit is illusory.  They could become more proficient in
R, **more quickly**, learning base-R than Tidy.

By the way, as noted below, the Tidy advocates don't like the many
base-R functions whose names *do* use English, e.g. **plot()**,
**lines()**,  **aggregate()** and **merge()**.  Clearly, then, English
is not the core issue.

### Pipes

The Tidyverse also makes heavy use of **magrittr** *pipes*, e.g. writing
the function composition **h(g(f(x)))** as

``` r
f(x) %>%  g() %>% h()
```

Again, the pitch made is that this is "English," in this case in the
sense of reading left-to-right.  But again, one might question just how
valuable that is, and in any event, I personally tend to write such code
left-to-right anyway, *without* using pipes:

``` r
a <- f(x)
b <- g(a)
h(b)
```

As a long-time teacher of programming languages (C, C++, Java, Pascal,
Python, R, assembly language, etc.), I find the promotion of pipes
troubling.  The piped version hides the fact that **g()** and **h()**
have an argument, which is invisible in the pipe expression.  This adds
confusion to the already-difficult process of learning the functions
concept.

Or if **w()** say, were to have two arguments, the first one being used
in the pipe, that argument would be hidden, making it appear that there
is only one argument:

``` r
> w <- function(u,v) u+2*v
> 3 %>% w(5)
[1] 13
```

Here **w()** has 2 arguments, but it looks like 1.

And what if we want that 3 to play the role of **v**, not **u**?  Yes,
**magrittr** has a way to do that, the "dot" notation:

``` r
> 3 %>% w(5,.)
[1] 11
```

But that is yet another example of my point, that **Tidy is burdening
the R learner with extra, unnecessary complexity**.  Indeed, just as
**dplyr**, with 263 functions, is far too complex for beginners, so are
pipes.  There are so many variations to learn that Hadley's *R for Data
Science* book devotes a full chapter to pipes, 3415 words.  

Granted, a beginner need learn only a small fraction of that
material at first, but the above example of the dot notation is
certainly not an advanced case.  Again, each time the beginner is
confronted with a new situation, she must sift through the myriad
variants, of **dplyr**, **purrr**, pipes or whatever.

Moreover, what if the function **h()** above has two arguments,
rather than just one, with each argument requiring functional
composition?  Pipes can't be used there.

And even more importantly, even advocates of pipes concede that pipes make
debugging more difficult; by contrast, my style above lends itself easily to
debugging.  And again, for large problems, piped code is slower.

The benefit of pipes claimed by the Tidyers is the "left to right"
execution.  They conceded that one can achieve this without pipes, but
stress that this comes at the expense of setting up variables for the
intermediate results.  That's a valid point, but is that small gain
worth the increased cognitive load on R learners, increased debugging
problems and so on?  To me it clearly is not.

### Code readability

The Tidyverse advocates also claim that the "English" in **dplyr** makes
the code easier to *read*, not just write.  To me, that is missing the
point; as any instructor of software engineering can tell you, the best
way to make code readable is to use REAL English, in good, meaningful
code comments.  And this is just as important, if not more so, for
nonprogrammers.

See my [R style guide](http://github.com/matloff/R-Style-Guide) for more on
readability issues.

