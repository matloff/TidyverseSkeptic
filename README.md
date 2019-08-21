# TidyverseSkeptic
An opinionated view of the Tidyverse "dialect" of the R language, and
its promotion by RStudio.

## Norm Matloff, Prof. of Computer Science, UC Davis (former Prof. of Statistics at UCD)


Note:  This essay is somewhat frank, involving the very
popular Tidyverse and RStudio. I hope it is polite and taken as
constructive criticism.  

I like and admire the RStudio people, including the Tidyverse
originator, Hadley Wickham, and have always supported them, both
privately and
[publicly](https://matloff.wordpress.com/2018/02/22/xie-yihui-r-superstar-and-mensch/).
I have been interacting with them from the beginning, when the firm
consisted of only founder JJ Allaire and ace developer Joe Cheng.  I
highly praise the firm to my students, and I use and recommend Hadley's
**ggplot2** package (though I don't consider it part of the Tidyverse,
having been developed well before Tidy and thematically unrelated). I
sometimes use **stringr**, and on occasion **devtools** has been an
absolute lifesaver for me.

In other words, I absolutely don't consider RStudio to be some evil
cabal.  I state at various places in this essay that I think their 
actions have been well-intentioned.  Nevertheless, I believe that
RStudio took a wrong turn when it decided to promote the Tidyverse,
which has led to a situation in which the very health of the language is
at stake.

[My bio is here.](http://heather.cs.ucdavis.edu/matloff.html)
Specifically in terms of R, I've been an R user and developer since near the 
beginning, having used R's predecessor S before that.  I've 
published several books that use R, and am currently (2019) the 
Editor-in-Chief of the *R Journal*.  (Hadley is a former EiC on the
journal.)

# Summary

1. The Tidyverse arose from the desire to have a set of packages that
   are consistent with each other, a "purist" philosophy that appeals,
for instance, to computer scientists.  The Tidyverse also borrows from
other "purist" computer science (CS) philosophies, notably *functional
programming*.  **The latter is abstract and theoretical,
difficult even for CS students, hence arguably an unwise approach for
nonprogrammer students of R.**

2.  **Another price of purity is increased complexity and
    abstraction**, making code more prone to error (as well as a
sacrifice in performance).  Ironically, though consistency of interface
is a goal, new versions of Tidy libraries are often incompatible with
older ones, a very serious problem in the software engineering world.

3. In heavily promoting the Tidyverse, especially in the education
   realm, RStudio, with its dominance in the R field, is developing an
entire new generation of R users whose skills in base-R are superficial
at best, and who -- most importantly -- feel that R *is* the Tidyverse.

4. The dominance of the commercial entity RStudio in an open-source
   project is key:  **It is NOT the case that Tidyverse rose to
prominence due to sheer quality in a free market of ideas.**  Hadley has 7
or 8 programmers working full time on Tidy, and as noted, RStudio
engages in aggressive educational outreach, heavily promoting Tidy.
This is not how open-source projects usually work, where participants
work in their free time.

5. **Regardless of being well-intentioned, RStudio is molding R into its
   own desired image.**  That new generation will come to dominate the
community, treating Tidyverse as the "real" base, and viewing the actual
base-R as something akin to assembly language.  One major RStudio
employee who asked to discuss this document with me referred to non-Tidy
packages as being in the legacy realm.  All this might be fine if the R
community were unified in viewing Tidyverse as a high-level improvement,
but many do not. They are not impressed by the syntax and so on, and as
noted, are worried about the slow performance of Tidy; some view Tidy as
a gimmick.

6.  That new generation will often be biased against non-Tidyverse job
    seekers, non-Tidyverse CRAN packages, and academics who submit
non-Tidyverse data science research papers and grant proposals.  **The
non-Tidiers will have no choice but to bend to RStudio's wishes.**  

7. For the above reasons, **RStudio is essentially operating as a
   monopolist.**  It's not a monopoly in the financial sense --
Tidyverse is not directly enhancing RStudio's profitability -- and, as
noted, is not intentional, but the result is classicly monopolistic, in
the sense of one product dominating a market, stifling innovation etc.
The adverse impacts are very serious and worsening.

8. One key example of the pernicious effects of this monopolistic
   situation is that RStudio's promotion of the Tidyverse has alarmingly
**impeded the progress and adoption of technologically superior packages**,
notably **data.table**. Most in the "Tidyverse generation" are unaware
of anything outside the Tidyverse.  For instance, Hadley's book, *R for
Data Science*, with Garrett Grolemund, barely mentions **data.table**.

9. A major reason offered by RStudio for promoting the Tidyverse is
    that it makes R easier to teach to non-programmers. They point out 
that this group will just be doing data analysis, rather than becoming
professional R programmers, and Tidy is a better vehicle for teaching
that.  **I would argue that, on the contrary, the Tidyverse makes R
*harder* to learn for this group.**

10. RStudio's development of the Tidyverse is a good thing, and those who
like its philosophy should use it.  One of R's biggest pluses is the
huge CRAN code repository, which I use heavily, and Tidyverse is a fine
addition to it.  My objection is in Point 6 above; I just don't want to
be forced to use Tidy. (As noted above, I also believe Tidy should not
be the "first language" presented in teaching R.) I would give as an
example the fact that R has various object-oriented programming (OOP)
paradigms to choose from, such as S3, S4 and R6.  I think it's great
that, e.g., R6 is available, but I don't want to be forced to use it.
(Just an example; both the Tidyverse and I use S3.)

11. **RStudio can easily remedy the situation.**  I have recommendations at
   the end of this essay.

# dplyr vs. data.table

The **dplyr** package is a featured app of the Tidyverse developed by
Hadley, so I'll use this as an example at several points in this essay.
(This is merely an example; **dplyr** vs. **data.table** is NOT the
primary theme of this essay.)

**Dplyr** borrowed a number of ideas from the earlier **data.table** by
Matt Dowle.  One of Hadley's major motivations was to give the user a
more "English-like" interface.  (Note: I regard both **dplyr** and
**data.table** as advanced topics; neither is suitable for beginners.)

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

![alt text](https://i0.wp.com/www.win-vector.com/blog/wp-content/uploads/2019/05/unnamed-chunk-1-2.png)

showing that **dplyr** can be extremely slow even relative to base-R,
thus even worse relative to **data.table**.

Matt's **data.table** package in a sense helped to "save" R.  At one
point there were major concerns that R could not handle Big Data, with
calls from some in favor of Python instead.  The **data.table** package
showed that R could do quite well in large datasets.  This really aided
in R's being adopted by various large companies, and likely played some
role in the creation of the R Consortium, which funds R projects.

Yet, RStudio, which as noted is heavily engaged in educational activities, 
both with its own courses and in interacting with teachers of R, has 
promoted its own product, **dplyr**, largely ignoring its rival,
**data.table**.  This is natural for a commercial entity, but in 
this case RStudio has a special responsibility as a dominant business in 
an open-source project. 

Hadley did develop an interface, **dtplyr**, but even this is 
[slow](http://www.win-vector.com/blog/2019/06/data-table-is-much-better-than-you-have-been-told/).

# Teachability

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
people who wish to use R for data analysis, not those who wish to become
professional R programmers.

### The Tidyverse advocates' claim

As a lifelong passionate teacher, I strongly question the claim made by
Tidyverse advocates that it facilitates the teaching of R to
non-programmers, as opposed to teaching them base-R.  (Again, I regard
both **dplyr** and **data.table** as advanced topics; neither is
suitable for beginners.)

There has been no study of this claim.  Advocates often provide
testimonials from students like "I learned R using Tidyverse, and now am
productive in R!" -- which says nothing at all about the teachability of
base-R in comparison.  (It is ironic that advocates who present such
statements are statisticians, who ought to know the need for a control
group.)

### Tidyverse makes learning harder, due to adding much complexity 

Contrary to the Tidy advocates' claim, I believe using the Tidyverse
makes things more *difficult* for learners without prior programming
background.  

Tidyverse students are being asked to learn a much larger volume of
material, which is clearly bad pedagogy.  See ["The Tidyverse
Curse"](https://www.r-bloggers.com/the-tidyverse-curse), in which the
author says *inter alia* that he uses "only" 60 Tidyverse functions --
60!  The "star" of the Tidyverse, **dplyr**, consists of 263
functions. 

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

As Matt Dowle [pointed
out](https://twitter.com/MattDowle/status/1142001162230489088),

> It isn't one function **mutate** that you combine in a pipe.  It's
> **mutate**, **mutate_**, **mutate_all**, **mutate_at**, **mutate_each**,
> **mutate_each_**, **mutate_if**, **transmute**, **transmute_**,
> **transmute_all**, **transmute_at** and **transmute_if**.  And you're
> telling me you don't need a manual to learn all those?

Having a common syntax thus does not compensate for this extensive
complexity.

By contrast, if this user knows base-R (not difficult), she can handle any
situation.  The old adage applies: "Give a man a fish, and he can eat
for a day. Teach him how to fish, and he can eat for a lifetime."

### The tapply() Function

One of the most commonly-used functions in R is **tapply()**.  As
noted below, for some reason Tidy advocates hate this function, but
arguably it is perfect for R beginnnrs.

Consider the **tapply()** function in base R.  A common example in
tutorials on the Tidyverse involves R's **mtcars** dataset.  The goal is
to find mean miles per gallon, grouped by number of cylinders.  The Tidy
code offered is

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
presented with some examples, beginner have no trouble using them in new
of similar type.

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
rather hard to read, while **tapply()** outputs a table.  the latter
form is exactly what many students need in their applications, e.g.
social science research.

Moreover, the **tapply()** output is more informative, letting the user
know that there were no 8-cyliner, 3-speed cars, again the kind of thing
that is quite meaningful in many applications of R.

### Use of functional programming

Another featured Tidyverse package, the *functional programming*
(FP)-oriented library **purrr**, has 177 functions.  Again the point
about complexity applies. Even more importantly, top university Computer
Science Departments have shifted away from teaching their introductory
programming courses using the FP paradigm, in favor of
the more traditional Python, as they deem FP to be more abstract and
challenging.  

An interesting discussion of the topic is in [Charavarty and
Keller](https://www-ps.informatik.uni-kiel.de/~mh/reports/fdpe02/papers/paper15.ps.gz).
Though they support using FP in introductory programming classes for CS
majors,  the authors' goals are antithetical to those of R learners.
The authors list three goals, one of which is to "Introduce the
essential [theoretical] concepts of computing," certainly not desirable
for teaching R in general, let alone for teaching R to those with no
coding experience.  They also concede that a key concept in FP,
*recursion*, is a "signficant obstacle" even for CS students.  

### Tibbles

Similarly, it is bad pedagogy to force students to learn tibbles, a
more complex technology, instead of data frames, a simpler one.  The
types of situations that tibbles are meant to address should be an
advanced topic, not for beginners with no coding background.

### The English issue

Again, the point most emphasized by Tidyverse advocates is that the
Tidyverse is more teachable because of its "English-like" syntax. 

Below is a comparison (adapted from
[here](https://atrebas.github.io/post/2019-03-03-datatable-dplyr/)):
We'll use R's built-in **mtcars** dataset.

``` r
mtdt <- as.data.table(mtcars)
mtdt[cyl == 6]  # data.table syntax
mttb <- as_tibble(mtcars)
filter(mttb,cyl == 6)  # dplyr syntax
```

Is there really any difference?  Can't beginners, even without
programming background, quickly adapt to either one after seeing a few
examples?  Even those who claim high teachability for **dplyr** do
readily agree that their students could also easily pick up
**data.table**, or for that matter my preference base-R, given some
examples.

And what of the fact that we have the English word *filter* above?
Granted, it looks nice, but English can be misleading or mystifying in a
computer context.  Even an experienced programmer would not be able to
guess what the **dplyr** function **mutate()** does, for instance.

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

And much more importantly, even advocates of pipes concede that pipes make
debugging more difficult; by contrast, my style above lends itself easily to
debugging.  And again, for large problems, piped code is slower.

Moreover, what if the function **h()** above has just two arguments,
rather than one?  Pipes can't be used there.

So, while I may agree with the Tidiers' preference for "left to right"
execution, it can be done without pipes (as I do), and I see no benefit
to them.

### Code readability

The Tidyverse advocates also claim that the "English" in **dplyr** makes
the code easier to *read*, not just write.  To me, that is missing the
point; as any instructor of software engineering can tell you, the best
way to make code readable is to use REAL English, in good, meaningful
code comments.  (And this is just as important, if not more so, for
nonprogrammers.)

### The diversity claim

One of the claims made by Tidyverse advocates -- indeed for many, the
*main* claim -- is that teaching R using Tidy makes learning easier for
women and minorities.  In essence, the view is that R must be "dumbed
down" for these groups.  As a long-time ardent, active supporter of social
justice, I find this claim insulting to women and minorities, and
again, not accurate.

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
Tidyverse, and some significant disadvantages.

I think it is a mistake to feature the Tidyverse in teaching R to
beginners, for these reasons:

1.  Complexity and volume of the presented material.

2.  Difficulty in debugging.

3.  Inadequate generalizability.

To me, the proper placement of Tidy in R courses should be:

* **dplyr:** Taught, along with **data.table**, at the Intermediate R
  level.

* **purrr:** Taught only at the Advanced level.

* pipes: Taught at the Intermediate level, for understanding code that
  uses it, but not recommended.

I am certainly not saying one should only use base R; on the
contrary, CRAN is a major advantage of R, which I use extensively.
But the Tidyverse should be considered advanced R, not for beginners,
just as is the case for most complex CRAN packages.

# R's Status As an Open-Source Language

### The Long Arm of RStudio

In the [SatRday LA conference](https://losangeles2019.satrdays.org/),
April 6, 2019, a speaker who was actually explaining the advantages of
**data.table** in large datasets said that package "was created by Matt
Doyle [sic].  Who's that?  No one knows who he is."  He repeated later,
"No one has ever heard of Matt Doyle."  Actually, many in the audience
had indeed heard of Matt Dowle, but in that speaker's world -- the
RStudio-educated world -- his statement about lack of name recognition
for Matt was sadly accurate.  Such is the impact of RStudio on the
field.

Hadley notes that base-R was mostly written 20 years ago.  Hadley's
[talk](https://t.co/7Ey27asCH4) in the 2016 useR! conference amounted to
a manifesto, calling for R to "modernize" along Tidy lines.  He conceded
that this would involve "short-term pain," yet believed it to be very
much worthwhile.  Again, given RStudio's dominance, this revolution in R
was sure to follow, which it has.
  
The Tidyverse is a vigorous promotional effort by RStudio that has come
to dominate the R world.  As mentioned, the firm has been especially
active in the education realm, including gifts of funding and licensed
software, and support for conferences.  It offers Tidy tutorials at all
R conferences, and so on.  Well-intentioned and useful, to be sure, but
with the conscious effect of increasing the firm's influence, and some
would argue, power.  

A good example of the intent of RStudio to bring all of R to the Tidy
world is the **broom** package (not written by RStudio, but featured on
their Web site).  Titled "Convert Statistical Analysis Objects into Tidy
Tibbles," its goal is to convert the output of numerous packages into
Tidy form.  I mentioned earlier a conversation with an RStudio employee
who views non-Tidy packages as legacy.

### The nature of support for the Tidyverse

"Testimonials" are legion.  Non-programmers who take Tidy-based R
courses are delighted that they can now do some data analysis, and
praise the Tidyverse without realizing they have no basis for comparison
to base-R, **data.table** and so on.  RStudio counts **ggplot2** as
being part of the Tidyverse, but it was developed much earlier, and does
not generally follow the Tidy philosophy.  But as a result of such
inclusion, I see many users who, being justly impressed with
**ggplot2**, mistakenly think that the package is Tidy
and thus is an advantage of being Tidy.  This illustrates the
mindset that has developed.

There is a Bandwagon Effect at work, not only for the Tidyverse but for
RStudio in general.  Many new R users, being educated in Tidy/RStudio,
assume both are "standard."  An
[interview](https://www.r-bloggers.com/heather-turner-the-user-2014-interview/)
of prominent R developer Heather Turner, for instance, gushes in
amazement that 

> Her description of how she accomplishes her work is fascinating –
> including the fact that she prefers Emacs over RStudio!

Similarly, many who teach R want to join Bandwagon as well, feeling they
must teach the "latest."

There is even behavior of the type one sees in cults.  I've seen
statements on Twitter from "graduates" of Tidyverse training who
actually apologize because their code did not use the Tidyverse.  One
post I saw came from a person who panicked with guilt because she had
written a **for** loop rather than employ Tidyverse's functional
programming package **purrr**.  In another tweet, the poster was angry
because there was a name conflict between a long-established R function
and one in the Tidyverse; he demanded that the original authors change
the name, oblivious to the fact that theirs long preceded Tidyverse.
Any criticism of the Tidyverse on Twitter is pounced upon by the
loyalists, often with vitriolic tones.  And they have mantras, e.g.
"Tidyverse showed me the fluidity of data!"  

One sees this especially in the Tidyiers' view of R's "apply" family of
functions.  For Tidy supporters, the biggest virtue is its English-like
syntax.  Yet ironically, the Tidyverse advocates' worst criticism of
base-R is aimed at functions that do have English names, the "apply"
family.  For some reason, **tapply()** is especially odious to them.  I
encounter many who proudly make a point of declaring that they would
never use any function from the "apply" family.  Such rigidity seems
irrational to me.

### Adverse Impact

Tidyverse advocate Roger Peng commented in his 2018 useR! address,
"It will be interesting to see how things evolve, and whether the
community can sustain multiple ways of programming.  I think that it
can, but that's my opinion." But this seems overly optimistic.

Given the dynamics described above, we will eventually, maybe rather
soon, reach a point at which most R users will be Tidy, and have indeed
"Never heard of Matt Dowle." 


This will make things very difficult for
the non-Tidy R people: Non-Tidy job seekers who are excellent R coders
will find that they are dismissed out of hand by Tidy interviewers;
authors of non-Tidy CRAN code will find their contribution is considered
useless; academics submitting data science research manuscripts or grant
proposals will find that Tidy reviewers give them low scores.  In short,
R will have to bend to RStudio's wishes.

For instance, the authors of 
[*Getting Started with R* (2nd ed.)](http://r4all.org/books/gswr2/)
stressed in [a
tweet](https://twitter.com/GSwithR/status/996830294367002625) that
their book is "Tidyverse compliant," and on their Web page note the
changes they made in their second edition:

> RStudio has emerged as a brilliant cross-platform interface to working
> with R. Furthermore, Hadley Wickham and colleagues, have developed
> several add-on packages including as dplyr, tidyr and ggplot2 that not
> only provide consistent and intuitive ways to work with your data, but
> are emerging as industry standards (academic and non-academic).

> We couldn’t afford to ignore these developments. The second edition
> thus dispenses entirely with classic methods of using R, and instead embraces
> RStudio along with dplyr, tidyr and ggplot2.

*This is classical monopolistic behavior.*  It's not a monopoly in the
financial sense, as Tidyverse is not directly enhancing RStudio's
profitability, and, as noted, is not intentional. But the result is
classicly monopolistic, in the sense of one product dominating a market.  

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
turned out to be model corporate citizens.

As noted, I know and admire the people at RStudio, *but a commercial
entity should not have such undue, unilateral influence on an
open-source project.*  

It should be noted that neither Hadley nor anyone else one from RStudio
is in the elite, 20-member R Core Group, which guides the development
of the language.  The Tidyverse thus is tantamount to an *end-run around
the leaders of this open-source project*.  As any expert in
organizational behavior will tell you, this does not augur well for the
future health of R, in spite of undoubtedly being well-intentioned.

RStudio is a great company, staffed by many talented people.  In my
opinion, their one failing has been to run off on their own, rather than
adhering to the norms of open-source projects.  

# Recommendations

In my view, RStudio can easily remedy the problem.  It can take the
following actions to greatly ameliorate the "monopolistic" problems:

1.  Promote the teaching of base-R to beginners, treating the Tidyverse
    as an advanced topic.  The popular book, *R for Everyone: Advanced
Analytics and Graphics* (second ed.), by Jared Lander does exactly this!

2.  In the various RStudio Web pages on writing fast R code, give
    **data.table** equal time.
