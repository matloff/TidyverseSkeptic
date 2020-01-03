# TidyverseSkeptic
An alternate view of the Tidyverse "dialect" of the R language, and
its promotion by RStudio.

## Norm Matloff, Prof. of Computer Science, UC Davis (former Prof. of Statistics at UCD)

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

In other words, I don't consider RStudio to be some evil cabal.  I state
at various places in this essay that I think their actions have been
well-intentioned.  Nevertheless, I believe that **RStudio took a wrong
turn when it decided to promote the Tidyverse**, which has led to a
situation in which the unity and health of the language is at stake.

[My bio is here.](http://heather.cs.ucdavis.edu/matloff.html)
Specifically in terms of R, I've been an R user and developer since near the 
beginning, having used R's predecessor S before that.  I've 
published several books that use R, and am currently (2019) the 
Editor-in-Chief of the *R Journal*.  (Hadley is a former EiC on the
journal.)

# SECTIONS:

* [Summary](#summ)

* [Tidyverse vs. ggplot2, stringr etc.](#notTidy)

* [dplyr vs. data.table](#dpt)

* [Teachability](#teachable) (to me, the most important issue) 

* [Diversity issues](#divers) 

* [R's Status as an Open-Source Language](#status)

* [Recommendations](#recs)

# <a name="summ"> </a> SUMMARY 

### Teachability

* My biggest concern is involves teaching of R.  **Tidy makes it more
  DIFFICULT for nonprogrammer learners of R to become proficient in the
language**.

* The Tidyverse arose from the desire to have a set of functions/packages that
   are consistent with each other, a "purist" philosophy that appeals,
for instance, to computer scientists.  The Tidyverse also borrows from
other "purist" computer science (CS) philosophies, notably *functional
programming* (FP).  The latter is abstract and theoretical,
**difficult even for CS students**, and thus it is clear 
**Tidy is an unwise approach for
nonprogrammer students of R.**

*  **Another price of purity is increased complexity and
    abstraction**, making code more prone to error (as well as a
sacrifice in performance).  

*  In fact, the **Tidyverse is general is far too complex for learners
    without prior coding background**, causing what psychologists call
<i>cognitive overload</i>.

*  Indeed, even many Tidy advocates concede that it is in various
    senses often more difficult to write Tidy code than base-R.  
Hadley says, for instance, "it may take a while to wrap your head around [FP]."

* Thus, contrary to the claim made by RStudio for promoting the Tidyverse is
    that it makes R easier to teach to non-programmers, 
**I would argue that, on the contrary, the Tidyverse makes R
*harder* to learn for this group.**

* RStudio has done an admirable job in bringing more women and
  underrepresented minorities into R.  Yet by saddling them with the
complicated Tidyverse system, RStudio has made it more difficult for
these groups to make contributions to the language, in the form of
writing CRAN packages, authoring books and so on.

### RStudio's role in R, an open source project

* Any economist -- or just plain common sense -- will tell you that
  RStudio's status as a moneyed commercial entity in a free, open source
project is bound to have profound changes on that project. 

* The dominance of the commercial entity RStudio in an open-source
  project is key:  **It is NOT the case that Tidyverse rose to
prominence due to sheer quality in a free market of ideas.**  Instead,
that prominence arose from heavy promotion by RStudio.  Hadley has 7 or
8 programmers working full time on Tidy, and RStudio engages in
aggressive educational outreach, promoting Tidy.  This is not how
open-source projects usually work, where participants work in their free
time.

* In heavily promoting the Tidyverse, especially in the education
   realm, RStudio, with its dominance in the R field, is developing an
entire new generation of R users whose skills in base-R are superficial
at best, and who -- most importantly -- feel that R *is* the Tidyverse.
This will shape the evolution of the language itself, in undesirable
ways.

* **Regardless of being well-intentioned, RStudio is molding R into its
   own desired image.**  That new generation will come to dominate the
community, treating Tidyverse as the "real" base, and viewing the actual
base-R as something akin to assembly language.  One RStudio principal
who asked to discuss this document with me referred to non-Tidy packages
as being in the "legacy" realm.  In other words, he expects that
all future packages will eventually be wrtten in Tidy. 

    All this might be fine if the R community
were unified in viewing Tidyverse as a high-level improvement, but many
do not. They are not impressed by the much-vaunted consistent syntax and
so on, and are worried about the slow performance of Tidy;
some view Tidy as a gimmick.

*  That new generation will often be biased against non-Tidyverse job
    seekers, non-Tidyverse CRAN packages, and academics who submit
non-Tidyverse data science research papers and grant proposals.  **The
non-Tidyers will have no choice but to bend to RStudio's wishes.**  Thus
RStudio is essentially operating as a monopolist.  It's not a monopoly
in the financial sense -- Tidyverse is not directly enhancing RStudio's
profitability -- and, as noted, is not intentional. But the result is
classicly monopolistic, in the sense of one product dominating a market,
stifling innovation etc.  The adverse impacts are very serious and
worsening.

* One key example of the pernicious effects of this monopolistic
   situation is that RStudio's promotion of the Tidyverse has alarmingly
**impeded the progress and adoption of technologically superior packages**,
notably **data.table**. Most in the "Tidyverse generation" are unaware
of anything outside the Tidyverse.  Hadley's book, *R for
Data Science*, with Garrett Grolemund, barely mentions **data.table**.

# <a name="notTidy"> </a> TIDYVERSE VS. GGPLOT2, STRINGR ETC.

RStudio bills the **ggplot2** graphics package as being part of the
Tidyverse.  Though again, as a commercial entity, this is a natural
marketing move on RStudio's part, it is inaccurate and misleading.

- Inaccurate, as **ggplot2** preceded Tidy by about 7 years, and does
  not use Tidy principles.  Hadley himself
[acknowledges this](https://community.rstudio.com/t/why-cant-ggplot2-use/4372),
noting that **ggplot2** is incompatible with pipes, a central Tidy
component, and he wishes he had designed the package around pipes.

- Unless one defines the Tidyverse to consist
of any package Hadley has ever written, inclusion of **ggplot2** in the
Tidyverse is factually incorrect.

- Misleading, because the (genuine) "Ooh! Ah!" qualtity of the
  **ggplot2** package "sells" beginners on the Tidyverse.  I often hear
them make statements like, "I love the Tidyverse, because I can create
nice graphics."  They don't realize that it's a non-Tidy package
that we non-Tidyers use all the time.

There are similar problems with RStudio presenting the **stringr**
package as Tidy, even though it predates Tidy by about 5 years, etc.

# <a name="dpt"> </a> DPLYR vs. DATA.TABLE

The **dplyr** package is a featured app of the Tidyverse developed by
Hadley, so I'll use this as an example at several points in this essay.

(This is merely an example; **dplyr** vs. **data.table** is NOT the
primary theme of this essay.  Note too that I regard both **dplyr** and
**data.table** as advanced topics; neither is suitable for beginners.)

**Dplyr** borrowed a number of ideas from the earlier **data.table** by
Matt Dowle.  One of Hadley's major motivations was to give the user a
more "English-like" interface (a point to which I'll return shortly).  

Unfortunately, **dplyr** is much, much slower than
**data.table** on large datasets.  Here are some of the
timing examples, for various operations, on the 
[H2O site](https://h2oai.github.io/db-benchmark/)
(times in seconds; see above URL for details):

<table border="1">
<tr>  <td>dplr</td>  <td>data.table</td>  </tr> 
<tr> <td>37.3</td>  <td>9.07</td> </tr>
<tr> <td>95.5</td>  <td>9.20</td> </tr>
<tr> <td>496</td>  <td>11.9</td> </tr>
</table>

The differences are even starker in
[this study](http://www.win-vector.com/blog/2019/05/timing-working-with-a-row-or-a-column-from-a-data-frame/)
by the consulting firm Win-Vec LLC, e.g.

<img src = "https://i0.wp.com/www.win-vector.com/blog/wp-content/uploads/2019/05/unnamed-chunk-1-2.png" height = "300">

showing that **dplyr** can be extremely slow even relative to base-R,
thus even worse relative to **data.table**.

**Matt's data.table package in a sense helped to "save" R**.  At one
point a few years ago there were major concerns that R could not handle
Big Data, with calls from some in favor of Python instead.  The
**data.table** package showed that R could do quite well in large
datasets.  This really aided in R's being adopted by various large
companies, and likely played some role in the creation of the R
Consortium, an industry-sponsored organizational that funds R projects.

Yet, RStudio, which as noted is heavily engaged in educational activities, 
both with its own courses and in interacting with teachers of R, has 
promoted its own product, **dplyr**, largely ignoring its rival,
**data.table**.  This is natural for a commercial entity, but in 
this case RStudio has a special responsibility as a dominant business in 
an open-source project. 

Hadley did develop an interface, **dtplyr**, but even this is 
[slow](http://www.win-vector.com/blog/2019/06/data-table-is-much-better-than-you-have-been-told/).  All sides agree that this is due to **dplyr** sticking to the FP approach.

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

### The Tidyverse advocates' claim

As a lifelong passionate teacher, I strongly question the claim made by
Tidyverse advocates that it facilitates the teaching of R to
non-programmers, as opposed to teaching them base-R.  (Again, I regard
both **dplyr** and **data.table** as advanced topics; neither is
suitable for beginners.  On the other hand, I think teaching beginners
**ggplot2** is fine, but point out again that it is not part of the
Tidyverse.)

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
functions, the high complexity is clear.  Every time a user needs some
variant of an operation, she must sift through those hundreds of
functions for one suited to her current need.  

Tidy advocates say the uniformity of interface in all those functions
makes learning them easier.  Uniform *syntax* is nice, yes, but the fact
remains that users must learn the *semantics* of the functions, i.e.
what operations they perform.  What, for example, is the difference
between **summarize()**, **summarize_each()**, **summarize_at()** and
**summarize_if()**?  Under which circumstances should each be used?  The
user must sift through this.

As [this excellent side-by-side tutorial](https://atrebas.github.io/post/2019-03-03-datatable-dplyr) notes, **data.table** consists of a single function that can be used in a highly versatile manner, while in **dplyr**,

> ...the syntax of dplyr is based on five main functions (filter(), arrange(),
> select(), mutate(), summarise()) and group_by() + their scoped variants
> (suffixed with _all, _at, or _if) + a bunch of helper functions.

That's a lot of functions to learn!

As Matt Dowle [pointed
out](https://twitter.com/MattDowle/status/1142001162230489088),

> It isn't one function **mutate** that you combine in a pipe.  It's
> **mutate**, **mutate_**, **mutate_all**, **mutate_at**, **mutate_each**,
> **mutate_each_**, **mutate_if**, **transmute**, **transmute_**,
> **transmute_all**, **transmute_at** and **transmute_if**.  And you're
> telling me [because of consistency of the user
> interfaces] you don't need a manual to learn all those?

Having a common syntax thus does not compensate for this dizzying
complexity.  As even one Tidy enthusiast
[conceded](https://twitter.com/tobar_with_R/status/1190974351060934657):

> ...when you come up with a clean, understandable code...you'll feel
> more rewarded

The poster concedes that coming up with a nice Tidy solution make
require some hard thinking.  Fine for an experienced R coder, but it
makes no sense to inflict this on the nonprogrammer R learner.  At their
stage, simplicity is key.

By contrast, if the user knows base-R (not difficult), she can handle any
situation.  The old adage applies: "Give a man a fish, and he can eat
for a day. Teach him how to fish, and he can eat for a lifetime."  The
same is true for **data.table**.

### What Tidy promoters want R beginners NOT to learn

The Tidyers make a point of avoiding the most basic parts of base-R:

* the '$' operator

* '[[ ]]'

* loops

* **plot()** and the associated basic graphics functions

They would argue that this "simplifies" the learning process, but
actually it forces beginners to come up with more complex, less
intuitive and harder-to-read solutions.

### Case Study: Redoing Dalgaard

Here is a quick example of the complexity of Tidy, and its consequent
unsuitability for use in teaching nonprogrammer learners of R.

A researcher tweeted in December 2019 that an introductory statistics
book by Peter Dalgaard is "now obsolete," because it uses base-R rather
than Tidy.  (Details later on in this essay.) I replied that I thought
the assertion that all books using R must now be revised to become
Tidy-compliant" was outrageous.  

I added that if he wished to use the book in his classes, he could write
up Tidy versions of the code from the book, and give it to his students
as a supplement.  Think what that would involve, how much extra
complexity it would add to the poor students.

Consider, for instance, an innocuous line like (not in the Dalgaard
book)

``` r
> hist(Nile)
```

i.e. drawing a simple histogram of R's built-in Nile dataset.  

This is something the instructor could have students do in the very
first lesson.  Easy!  By contrast, the Tidy crowd forbids use of base-R
plots, insisting on using **ggplot2** (which again is not Tidy, but is
considered as such by the Tidy advocates).  To be Tidy
the instructor would have to do something like

``` r
> library(ggplot2)
> dn <- data.frame(Nile)
> ggplot(dn) + geom_histogram(aes(Nile),dn)
```

Here the instructor would have a ton of things to explain -- packages,
data frames, **ggplot()**, the **aes** argument and so on -- 
and thus she could definitely NOT present it in the first lesson.

Here's an example from the book:

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

### Case Study: the tapply() Function

One of the most commonly-used functions in R is **tapply()**.  As
noted below, for some reason Tidy advocates hate this function, but
arguably it is perfect for R beginners.

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
presented with some examples, beginners have no trouble using them in a
new setting of similar type.  The Tidy version requires two function
calls rather than one for base-R.  But again, both versions are simple,
so let's call it a tie.  But is it certainly not the case that the Tidy
version is *easier* to learn.

It's instructive to look at what happens when one groups by two aspects:

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
group:

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

Note the need to convert to factors, something not mentioned in the
Tidy documentation, and which would further complicate things for R
beginners even if it were documented.

So, in terms of clarity and learnability, the Tidy and base-R versions
in this paricular example are both good, again showing that Tidy is not
easier to learn.  And In terms of usability, I'd give base-R the win
here. 

### Use of functional programming

Another featured Tidyverse package, the *functional programming*
(FP)-oriented library **purrr**, has 177 functions.  Again the point
about complexity applies;  we again have the "too many functions to
learn" problem as we saw with **dplyr** above.  

At the basic level, FP is merely replacing loops by calls to FP
functions.  R's **apply** family, plus **Reduce()**, **Map()** and
**Filter()** should be considered FP.  In many cases, using such
functions is the right solution.  But the indiscriminate use of FP,
advocated by many Tidyers, to replace *all* loops is clearly overdoing
it, and makes things especially difficult for beginners.

This is clear *a priori* -- **FP involves writing functions, a skill that
most beginners take a long time to develop well.**

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
experienced R programmer*.  But again, it's wrong to foce nonprogrammer
learners of R to "wrap their heads around" **purrr**.

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

* The R learner here must learn two different map functions for this
  particular example, and a dozen others for even basic use. This is an
excellent example of Tidy's cognitive overload problem.  Actually,
**purrr** has 52 different map functions!  (See below.)

* The first '~' in that first map call is highly nonintuitive.  Even
  experienced programmers would not be able to guess what it does. This
is starkly counter to the Tidyers' claim that Tidy is more intuitive and
English-like.

* Tidy, in its obsession to avoid R's standard '$' symbol, is causing
  all kinds of chaos and confusion here.

    The hapless student would naturally ask, "Where does that expression
'summary' come from?"  It would appear that **map()** is being called on
a nonexistent variable, **summary**.  In actuality, base-R's
**summary()** function is being called on the previous computation
behind the scenes.  Again, highly nonintuitive, and NOT stated in the
online help page.

    The poor student is further baffled by the call to **map_dbl()**.
Where did that 'r.squared' come from?  Again, Tidy is hiding the
fact that **summary()** yields an S3 object with component
**r.squared**.  Yes, sometimes it is helpful to hide the details, but
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

Exactly my point!  **Newbies should write this as a loop, NOT using
purrr**.  But the Tidy promoters don't want learners to use loops.
So the instructor using Tidy simply would avoid giving students such an
example, whereas it would be easy for the base-R instructor to do so.

As noted, the Tidy version shown earlier  is an illustration of the "too
many functions to learn," cognitive overload, problem we saw earlier
with **dplyr**.  Behold:

``` r
> ls(package:purrr,pattern='map*')
 [1] "as_mapper"      "imap"           "imap_chr"       "imap_dbl"      
 [5] "imap_dfc"       "imap_dfr"       "imap_int"       "imap_lgl"      
 [9] "imap_raw"       "invoke_map"     "invoke_map_chr" "invoke_map_dbl"
[13] "invoke_map_df"  "invoke_map_dfc" "invoke_map_dfr" "invoke_map_int"
[17] "invoke_map_lgl" "invoke_map_raw" "lmap"           "lmap_at"       
[21] "lmap_if"        "map"            "map_at"         "map_call"      
[25] "map_chr"        "map_dbl"        "map_depth"      "map_df"        
[29] "map_dfc"        "map_dfr"        "map_if"         "map_int"       
[33] "map_lgl"        "map_raw"        "map2"           "map2_chr"      
[37] "map2_dbl"       "map2_df"        "map2_dfc"       "map2_dfr"      
[41] "map2_int"       "map2_lgl"       "map2_raw"       "pmap"          
[45] "pmap_chr"       "pmap_dbl"       "pmap_df"        "pmap_dfc"      
[49] "pmap_dfr"       "pmap_int"       "pmap_lgl"       "pmap_raw"      
```

By contrast, in the base-R version, we indeed stuck to base-R!  There
are only four main functions to learn in the 'apply' family:  **apply()**,
**lapply()**, **sapply()** and **tapply()**.

### Tibbles

Similarly, it is bad pedagogy to force students to learn tibbles, a
more complex technology, instead of data frames, a simpler one.  The
types of situations that tibbles are meant to address should be an
advanced topic, not for beginners with no coding background.

Those advanced situations involve data frames in which row/column
elements are not *atomic* objects, i.e.\ not simple numbers, character
strings or logical values.  **This is a "straw man" set up by the Tidy
advocates'**; R beginners are very unlikely to encounter data frames of
this type.

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
have an argument, which is invisible in the pipe expression.  

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

As noted before, a beginner need learn only a small fraction of that
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

### Summary:  the proper status of the Tidyverse in teaching

As I said earlier, in discussions with those who report success in using
the Tidyverse to teach beginning programmers, I ask whether their
students are incapable of learning just base-R.  They readily concede
that the answer is no.  Indeed, before the Tidyverse, throngs of people
were learning base-R without any prior programming background.

As also mentioned, the Tidyverse can be difficult to debug, and run very
slowly on large datasets.  The perceived benefit of being "English-like"
is illusory.

In short, in my view there is no advantage to teaching R through the
Tidyverse, and some significant disadvantages.  I think it is a mistake
to feature the Tidyverse in teaching R to beginners, for these reasons:

1.  Complexity and volume of the presented material.

2.  Difficulty in debugging.

3.  Inadequate generalizability.

# <a name="divers"> </a> DIVERSITY ISSUES

Around the mid-2010s, RStudio began a major effort to bring more women
into R.  Later, they also added underrepresented minorities to this,
but their focus remains on gender, especially in its support of the R
Ladies groups.

The firm deserves major credit for this.  There are, however, two
concerning issues here:

* One of the claims made by Tidyverse advocates -- indeed for many, the
*main* claim -- is that teaching R using Tidy makes learning easier for
women and minorities.  One often sees R Ladies workshops promoting Tidy, and
frequent claims along the lines of "The Tidyverse has brought large
numbers of women and underrepresented groups into R."

    In essence, the view is that R must be "dumbed down" for these groups.
As a long-time ardent, active supporter of social justice, I find this
claim insulting to women and minorities, and again, not accurate.

* By especially promoting Tidy to women and minorities, RStudio is
  making it more difficult for these groups to make real contributions
to R.  It is impossible for someone to write a CRAN package or write an
R book without solid knowledge of base-R.

# <a name="status"> </a> R'S STATUS AS AN OPEN-SOURCE LANGUAGE

### The Long Arm of RStudio

*Ignorance of the non-RStudio world:*

In the [SatRday LA conference](https://losangeles2019.satrdays.org/),
April 6, 2019, a speaker who was actually explaining the advantages of
**data.table** in large datasets said that package "was created by Matt
Doyle [sic].  Who's that?  No one knows who he is."  He repeated later,
"No one has ever heard of Matt Doyle."  Actually, many in the audience
had indeed heard of Matt Dowle, but in that speaker's world -- the
RStudio-educated world -- his statement about lack of name recognition
for Matt was sadly accurate.  Such is the impact of RStudio on the
field.

*Huge promotion efforts by RStudio:*

Hadley notes that base-R was mostly written 20 years ago.  Hadley's
[talk](https://t.co/7Ey27asCH4) in the 2016 useR! conference amounted to
a manifesto, calling for R to "modernize" along Tidy lines.  He conceded
that this would involve "short-term pain," yet believed it to be very
much worthwhile.  Again, given RStudio's dominance and zealous promotion
of Tidy, this revolution in R was sure to follow, which it has.
  
The Tidyverse is a vigorous promotional effort by RStudio that has come
to dominate the R world.  As mentioned, the firm has been especially
active in the education realm, including gifts of funding and licensed
software, and support for conferences.  It offers Tidy tutorials at all
R conferences, and so on.  Well-intentioned and useful, to be sure, but
with the conscious effect of increasing the firm's influence, and some
would argue, power.  Some prominent figures in the R community who are
beholden to RStudio or otherwise need to stay in the firm's good graces,
keep their negative opinions of the Tidyverse quiet.

A good example of the intent of RStudio to bring all of R to the Tidy
world is the **broom** package (not written by RStudio, but featured on
their Web site).  Titled "Convert Statistical Analysis Objects into Tidy
Tibbles," its goal is to convert the output of numerous packages into
Tidy form, i.e. to "Tidy-fy" R.  I mentioned earlier a conversation with
an RStudio principal who views non-Tidy packages as "legacy."

### The nature of support for the Tidyverse

*Testimonials:*

"Testimonials" are legion.  Non-programmers who take Tidy-based R
courses are delighted that they can now do some data analysis, and
praise the Tidyverse without realizing they have no basis for comparison
to base-R, **data.table** and so on.  

As mentioned earlier, RStudio counts **ggplot2** as being part of the
Tidyverse, but it was developed much earlier, and [does not generally
follow the Tidy
philosophy.](https://community.rstudio.com/t/why-cant-ggplot2-use/4372)
But as a result of such inclusion, I see many users who, being justly
impressed with **ggplot2**, mistakenly think that the package is Tidy
and thus is an advantage of being Tidy.  This illustrates the mindset
that has developed.

*A Bandwagon Effect:*

There is a Bandwagon Effect at work, not only for the Tidyverse but for
RStudio in general.  Many new R users, being educated in Tidy/RStudio,
assume both are "standard," and anything from RStudio is unquestioningly
accepted as the proper way to do things.  

One example of this view of RStudio as the "industry standard" arose in
an [interviewe](https://www.r-bloggers.com/heather-turner-the-user-2014-interview/)
of prominent R developer Heather Turner, where the interviewe gushed in
amazement that 

> Her description of how she accomplishes her work is fascinating –
> including the fact that she prefers Emacs over RStudio!

shocked that a major figure in R would not use RStudio.  Similarly, many
who teach R want to join Bandwagon as well, feeling they must teach the
"latest" (or as noted, the perceived "industry standard").

As noted, some analysts like the Tidyverse from a theoretical point of
view, such as a conviction that functional programming is the best
approach to coding.  But for many others, Tidy is indeed a Bandwagon
that they jump blindly, without understanding the issues.

At the aforementioned SatRday conference, for instance, one of the
speakers was a recent math graduate, now working in the business world.
She emphasized that she likes functional programming because she can
view it as the concept of functional composition in math, as in the
above example **h(g(f(x)))**.  But as explained in our discussion of
pipes above, the claimed benefit of pipes is that one can use them to
AVOID doing functional composition.

This blind faith extends to other RStudio products, such as RMarkdown.
One Tidy follower on Twitter, for example, mistakenly thought that one
cannot write reproducible code -- code that give the same result no
matter when or where it is run -- unless one uses RMarkdown.  This of
course is quite false; RMarkdown is neither necessary nor sufficient for
reproducibility.  But the poster had apparently heard "Use RMarkdown for
reproducibilty," and took it more literally than even RStudio meant it.

One sees this especially in the Tidyers' view of R's "apply" family of
functions.  For Tidy supporters, the biggest virtue is its English-like
syntax.  Yet ironically, the Tidyverse advocates' worst criticism of
base-R is aimed at functions that do have English names, the "apply"
family.  For some reason, **tapply()** is especially odious to them.  I
encounter many who proudly make a point of declaring that they would
never use any function from the "apply" family.  Such rigidity seems
irrational to me, and symptomatic of the mentality that has developed.

*Cult-like behavior:*

There is often behavior of the type one sees in cults.  I've seen
statements on Twitter from "graduates" of Tidyverse training who
actually apologize because their code did not use the Tidyverse.  One
post I saw came from a person who panicked with guilt because she had
written a **for** loop rather than employ Tidyverse's functional
programming package **purrr**.  In another tweet, the poster was angry
because there was a name conflict between a long-established R function,
**select()**, and one in the Tidyverse; he demanded that the original
authors change the name, oblivious to the fact that theirs long preceded
Tidyverse.  As is typical with cults, they have mantras, e.g.
"Tidyverse showed me the fluidity of data!"  When asked what the mantras
mean, many cannot offer an explanation.  

### "Circle the wagons" behavior

Any criticism of the Tidyverse in Twitter is pounced upon by the
loyalists, often with vitriolic tones.  Granted, Twitter is a
rough-and-tumble forum, but sadly, some in RStudio itself have
Twitter-blocked some of the critics, abruptly ending frank but civil
conversation.  In my case, one major RStudio developer [made quite a
show of it](https://twitter.com/romain_francois/status/1140860812837445632?s=19),
tweeting a screen shot in which "You have blocked this user" is repeated
dozens of times.  **Given RStudio's considering itself a leader in the R
community, such childish, spiteful behavior is improper and
counterproductive.**

### Adverse Impact

Tidyverse advocate Roger Peng commented in his 2018 useR! address,
"It will be interesting to see how things evolve, and whether the
community can sustain multiple ways of programming.  I think that it
can, but that's my opinion." But this seems overly optimistic.

Given the dynamics described above, we will eventually, maybe rather
soon, reach a point at which most R users will be Tidy, and have indeed
"Never heard of Matt Dowle." 

This will make things very difficult for the non-Tidy R people: Non-Tidy
job seekers who are excellent R coders will find that they are dismissed
out of hand by Tidy interviewers; authors of non-Tidy CRAN code will
find their contribution is considered useless; academics submitting data
science research manuscripts or grant proposals will find that Tidy
reviewers give them low scores.  In short, R will have to bend to
RStudio's wishes.

For instance, the [R4All](http://r4all.org/) authors of 
[*Getting Started with R* (2nd ed.)](http://r4all.org/books/gswr2/)
stressed in [a
tweet](https://twitter.com/GSwithR/status/996830294367002625) that
their book is "Tidyverse compliant," and on their Web page note the
changes they made in their second edition (emphasis added):

> RStudio has emerged as a brilliant cross-platform interface to working
> with R. Furthermore, Hadley Wickham and colleagues, have developed
> several add-on packages including as dplyr, tidyr and ggplot2 that not
> only provide consistent and intuitive ways to work with your data, but
> are emerging as **industry standards** (academic and non-academic).

> We couldn’t afford to ignore these developments. The second edition
> thus dispenses entirely with classic methods of using R, and instead embraces
> RStudio along with dplyr, tidyr and ggplot2.

Similarly, a statement by the "bootcamp" Dataquest:

> Longtime Dataquest users may know that we’ve actually offered R
> courses for some time, but our old courses weren’t up to **modern R
> standards**.  They didn’t make use of popular tidyverse packages like
> ggplot2 or teach students to work in RStudio, but these skills are now
> **industry-standard** for doing data science with R...

(Note the false characterization of **ggplot2** as being part of the
 "Tidyverse.")

In a [December 2019
tweet](https://twitter.com/kaz_yos/status/1203408440607068163), a
researcher wrote about a popular book, *Introductory Statistics with R*
by Peter Dalgaard,

> This now obsolete book was my introduction to biostatistics and R. I’m
> not sure if there is a better book with epidemiologically oriented
> examples these days.

This is especially remarkable in that it's a book on *statistics*, not
R.  The R language only plays a supporting role.  Thus the notion that
this book is now "obsolete" is shocking, and untenable.

*This is classical monopolistic behavior.*  It's not a monopoly in the
financial sense, as Tidyverse is not directly enhancing RStudio's
profitability, and, as noted, is not intentional. But the result is
classicly monopolistic, in the sense of one product dominating a market,
and attendant ills. 

A highly insidious consequence of monopolies is the stifling of
innovation.  The case of **data.table** discussed above is a fine case
in point.

An open-source project involves a people spending a large amount of time
developing the project for free, no pay. Thus, for a commercial entity
to then swoop down and exploit all that free labor for its own profit is
fraught with peril.  To then take over the product as its own
is unconscionable.  I have no doubt that RStudio was well-intentioned in
this, sincerely believing in the Tidyverse, but many do not share this
view, and RStudio should have worked with the R Core Group (see below),
rather than taking action on its own.

The first major firm to become involved in R was Revolution Analytics
(now part of Microsoft).  There was much concern in the R community at
the time over Revo's potential negative impact on R, but instead, they
turned out to be model corporate citizens.  Ever since they began
heavily promoting the Tidyverse, RStudio has failed this criterion.

As noted, I know and admire the people at RStudio, *but a commercial
entity should not have such undue, unilateral influence on an
open-source project.*  

It should be noted that neither Hadley nor anyone else one from RStudio
is a memner of the elite, 20-member R Core Group, which guides the development
of the language.  The Tidyverse thus is tantamount to an *end-run around
the leaders of this open-source project*.  As any expert in
organizational behavior will tell you, this does not augur well for the
future health of R, in spite of undoubtedly being well-intentioned.

RStudio is a great company, staffed by many talented people.  In my
opinion, their one failing has been to run off on their own, rather than
adhering to the norms of open-source projects.  

# <a name="recs"> <a/> RECOMMENDATIONS

*Teaching:*

Courses in R, **especially those aimed an nonprogrammers**, should
develop a solid grounding in base-R as first priority.

The proper placement of Tidy in R courses should be:

* **dplyr:** Taught, along with **data.table**, at the Intermediate R
  level.

* **purrr:** Taught only at the Advanced level.

* pipes: Taught at the Intermediate level, and presented as an *option*
  that some students may find useful in some situations (as opposed to
being presented as *the* way one should work).

I am certainly not saying one should only use base R; on the
contrary, CRAN is a major advantage of R, which I use extensively,
and to which R beginners should definitely be exposed.

But the Tidyverse should be considered advanced R, not for beginners,
just as is the case for most complex CRAN packages, and should be
presented, as noted, as an *option*, not as *they* way.

*The role of RStudio:*

In my view, RStudio can easily remedy the problem.  It can take the
following actions to greatly ameliorate the "monopolistic" problems:

1.  Promote the teaching of base-R to beginners, treating the Tidyverse
    as an advanced topic.  The popular book, *R for Everyone: Advanced
Analytics and Graphics* (second ed.), by Jared Lander does exactly this!

2.  In the various RStudio Web pages on writing fast R code, give
    **data.table** equal time.
