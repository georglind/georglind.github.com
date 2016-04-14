---
layout: post
title: "Non-standard Analysis"
date: 2015-11-12 09:00
comments: True
categories: [Mathematics, Education]
---

Physicists! Bah...! They deal with mathematics on a needs come, needs serve basis. They regularly divide with infinitesimals, mindlessly exchange the order of integration and differentiation and carelessly sum only parts of an infinite series expansion. Rigor is dead and buried as long as they end up with meaningful and useful answers!

But isen't it weird that while the road to becoming a theoretical physicist includes numerous rigorous math courses like Algebra, Measure theory, Geometry, and Analysis, then most physicists still opt for the shortcut and get away with it?

Here we will take an interest in the field of mathematical analysis, that investigates mathematical functions, their derivatives and integrals by dealing with the infinitely small. The point of this post is to emphasize that rigor can take on more or less pedagogical forms by exploring a little known but perhaps more intuitive reformulation of mathematical analysis, known as the hyperreals&hellip;

### A Historical Prelude

Historically, the idea of taking something quite small, but finite, and then turn it infinitely small has been employed by many mathematicians throughout the ages, including works by [Archimedes](https://en.wikipedia.org/wiki/The_Method_of_Mechanical_Theorems), [Fermat](https://en.wikipedia.org/wiki/Adequality), [Euler](https://en.wikipedia.org/wiki/Introductio_in_analysin_infinitorum), Bolzano, and Cauchy. The greatest result of this approach is calculus, where first Newton and especially Leibniz introduced positive quantities smaller than any real number and called them "fluxions" or "infinitesimals". 

But, infinitesimals ended up making serious formalistic mathematicians, aka David Hilbert, uneasy. Infinity and infinitesimals do not represent real numbers. So, how can we do calculations with numbers that do not exist? It was Karl Weierstrass, who followed up on the work of [Bolzano](https://en.wikipedia.org/wiki/Bernard_Bolzano#Mathematics), and answered this riddle by getting completely away with the infinitesimals. Instead he introduced the concept of limits and the method of epsilon-delta reasoning -- a method so strong that it is currently being celebrated in every calculus textbook and in many Analysis-101 courses. 

However, I'm sure that most people (phycisits included) have felt that this rigid approach to calculus could not be the full story. How was a successful tool like calculus built on such a shaky ground? And how did it manage to stand there majestically for centuries until somebody eventually took the time to secure the foundations? And how can it be that all the physics shortcuts have not left physicists in a logic-less ruin?

[Abraham Robinson](https://en.wikipedia.org/wiki/Abraham_Robinson) was the first to consider taking the concept of infinitesimals seriously. He expanded the field of real numbers with  unlimited numbers (the infinite) as well as infinitesimals. He needed a fancy name for his contrsuction, and today it is known as the *field of the hyperreal*. We are going to take a close look at it, following the most common approach based on something called *ultrafilters*.

## Ultrafilters

For the construction of the hyperreals we need *ultrafilters*. They will help us ensure that the hyperreals is a well-ordered field of numbers. 

And **no**, I have no idea why they are called ultrafilters&hellip;

{% img center /files/nonstandard_analysis/ultrafilter.png 'Ultrafilter' 'Ultrafilter' %}

No matter&hellip; A free ultrafilter $U$ on the natural numbers, $\mathbb{N}$, is a set of subsets of $\mathbb{N}$ with the properties that,

1. $U$ only contains infinite subsets of $\mathbb{N}$.
2. For two elements in $U$ (let us call them $X\_1$ and $X\_2$), the intersection of those two sets must also belong to $U$, so $X\_1 \cap X\_2 \in U$.
3. Consider some infinite subset $X\_1$ which belongs to $U$. All supersets of $X\_1$ (all $X\_2 \supset X\_1$) then also belongs to this ultrafilter.
4. If $X \notin U$ then the complement of $X$ \(written as $\mathbb{N} \setminus X$\) belongs to $U$. 

As a simple example consider the empty set $\emptyset = \\{\\}$. The empty set is finite and does *not* belong in an ultrafilter (per statement 1). The complement of the empty set (which is the full set $\mathbb{N} \setminus \emptyset = \mathbb{N}$) then instead belongs to $U$ (per statement 4).

On the other hand: Consider the infinite subset containing all the even numbers, $\mathbb{N}_e$, and the subset containing all the odd numbers, $\mathbb{N}_o$. The intersection of those two subsets $\mathbb{N}_e \cap \mathbb{N}_o = \emptyset$, meaning that they cannot both belong to our ultrafilter (per statement 2). Because the two sets are the complements of each other, exactly *one* of them must belong to $U$ (per statement 4), but we are free to choose which one!

So an ultrafilter is not unique, but it can be shown that two ultrafilters on the same set are equivalent, and one can be constructed from the other simply by exchanging some elements with their complements.

## The hyperreals

After this small intermission, we are ready to construct the hyperreals. This particular construction uses sequences. A sequence is a function on the positive integers, and we write them in the following way,

$$ \underline{a} = (a_1, a_2, a_3, \ldots) = \big( a_j \big)_{j=1}^\infty = ( a_j ) $$

The hyperreals are constructed from infinite sequences on the reals, $\underline{a} \in \mathbb{R}^{\mathbb{N}}$. The real numbers themselves can easily be represented as infinite sequences with constant elements,

$$ \underline{x} = (x) = (x, x, x, \ldots). $$

So the number 2 is written,

$$ (2) = (2, 2, 2, \ldots) $$

But we may dream up many other "non-real" sequences, like these: 

$$ (0, 1, 0, 1, 0, \ldots) \text{ or } (1, 2, 3, 4, 5, 6, \ldots).$$

We want the hyperreal numbers to be ordered, so any two hyperreal numbers can be compared and found to be either larger or smaller than each other. The main problem with our sequences is that they cannot be compared to each other in a consistent way. Is $$ (1, 2, 3, 4, 5, \ldots) $$ greater or smaller than $$(2, 2, 2, 2, \ldots)$$? And what about $$ (0, 1, -1, 2, -2, 3, -3, \ldots)$$ compared to $$(1, 1, 2, 1, 1, 2, \ldots)$$? If I change a single element of a sequence, is this new sequence then greater, smaller or equivalent to the original sequence?

In order to extract something usable, we must "thin out" in the forest of possible sequences.

We do this by letting two sequences represent the same hyperreal number if "most" of their elements are identical. For a consistent definition of "most" we return to the ultrafilter construction. We say that two sequences are equivalent, $\underline{r} \equiv \underline{s}$, if and only if the places, at which they share elements, form an infinite set that belongs to our ultrafilter, $U$:

$$\langle r = s \rangle = \{j \in \mathbb{N}: r_j = s_j\} \in U.$$

Note that we sneakily introduced the parenthesis $\langle \cdots \rangle$, to signify that we are transforming a relation between two sequence representations of hyperreal numbers into a set of indices for which the sequence elements obey that same relation.

Using the properties of the ultrafilter, it is easy to show that this construction is transitive and defines an equivalence relation. The resulting equivalence classes define the *hyperreals*:

$$ *\mathbb{R} = \{ [r] \, : \, r \in \mathbb{R}^\mathbb{N} \} $$

Hyperreal numbers may be manipulated by first choosing sample sequences from the relevant equivalence classes, then performing element-wise operations on those sample sequences, and finally representing the resulting hyperreal as the equivalence class of the resulting sequence. If that was too convoluted, here comes the simple definitions of addition and multiplication,

$$ r \oplus s =  [r] + [s] = [(r_j + s_j)]$$

$$ r \odot s = [r] \cdot [s] = [(r_j \cdot s_j)] $$

We are now ready to show that this careful construction allow us to order the hyperreals. Assume that one sequence, $r$, for "a large part" is smaller than another sequence, $s$. Again we take "for a large part" to mean that the sequence indices at which $r$ is smaller than $s$ belong to our ultrafilter, so $\langle r < s \rangle =  \\{ j : r_j < s_j \\} \in U$. It follows almost automatically that $r \not\equiv s$, because $\langle r = s \rangle \subset \mathbb{N} \setminus \langle r < s \rangle \not\in U$ (by use of ultrafilter properties 1 and 4). 

When applied a little more rigorously this shows that the hyperreals, $(\*\mathbb{R}, \oplus, \odot)$, indeed form an *ordered field*.

### The reals

As we already anticipated, the real numbers are embedded in the hyperreals represented by classes equivalent to the constant sequences. Let us introduce a map from the reals to the hyperreals, $* : \mathbb{R} \rightarrow *\mathbb{R}$, such that

$$ *x = [\underline{x}] = [(x, x, x, \ldots)] $$

We refer to these hyperreal numbers as *standard*. They directly equip the hyperreals with neutral elements for addition, $\*0$, and multiplication, $\*1$.

You may remember this alternating sequence, we looked at earlier:

$$ (0, 1, 0, 1, 0, 1, \ldots ),$$

It directly exhibits the cleverness of the ultrafilter construction. This sequence overlaps with the real number $\*0$ on all the even sites, and with the real $\*1$ on all the odd sites. From our discussion of ultrafilters, we know that the set of even numbers, $\mathbb{N}_e$, and the set of odd numbers, $\mathbb{N}_o$ *cannot* belong to the same ultrafilter. This means that for some choice of ultrafilter, the alternating sequence will belong to the $\*0$ equivalence class, and in others it may belong to the $\*1$ class.

### Infinitesimals

The hyperreals also contain a lot of numbers in the vicinity of the standard numbers. Consider for example the hyperreal $s = [\underline{s}]$ defined by the sequence,

$$ \underline{s} = (r + 1/j)_{j=1}^\infty $$

This sequence only intersects sample sequences from the standard number classes a *finite* number of times. This makes the corresponding hyperreal number, $s = [\underline{s}]$, decidedly *non-standard*. It is easy to show that $\langle *x < s \rangle = \mathbb{N}$. More interestingly $s$ squeezes in between $\*x$ and any other standard number $y > x$, because $\langle s < y \rangle \in U$. 

The difference between those two hyperreal numbers, $s - \*x$, is now smaller than any positive real number, and we may refer to it as *infinitesimal*. There exists a whole plethora of well-ordered infinitesimals, and they can be compared to each other, so one is smaller and one is bigger, even though they are all infinitesimal. When two hyperreal numbers, $s$ and $r$, are (only) separated by an infinitesimal, we write that $s \simeq r$. 

We can then introduce two useful functions. The *halo* of a hyperreal contains the infinitesimal cloud around the closest standard number,

$$\mathrm{hal}(r) = \{ s \in *\mathbb{R} : s \simeq r\} $$

Similarly, we say that two hyperreals, $s$ and $r$, are limited separated whenever their distance is *not* an infinitesimal, and we write $s \sim r$. The classes of this equivalence relation are called the *galaxies*, and we write.

$$\mathrm{gal}(r) = \{ s \in *\mathbb{R} : s \sim r \} $$

We may take a look at the hyperreal infinitesimals through the *infinitesimal microscope*&mdash;a pedagogical representation of the hyperreal number line originally introduced by Jerome Keisler. Focusing on a particular hyperreal, $r$, the microscope magnifies its halo:

{% img center /files/nonstandard_analysis/microscope-01.png 'The infinitesimal microscope' 'The infinitesimal microscope' %}

### Unlimited numbers

The unlimited numbers form another interesting family of hyperreal numbers. Consider for example the hyperreal number represented by,

$$ n = [\underline{n}] = [(1, 2, 3, 4, 5, \ldots )]. $$

It is clearly non-standard (its sample sequences only overlap real number sequences at a finite number of places), and it is also greater than any real number: All properties which we normally associate with the infinite. However, like the infinitesimals, there are many *different* unlimited numbers within the hyperreals. Consider for example:

$$ m = [\underline{m}] = [(2, 3, 4, 5, 6, \ldots)]. $$

Here $m$ is also unlimited, and in addition $m > n$, which may confuse or comfort you, depending on your mathematical standpoint.

## Hey, wait a minute...

What have we just done? It seems we have taken the [Cauchy sequences](https://en.wikipedia.org/wiki/Cauchy_sequence) and turned those sequences into numbers themselves... or entities? Is that all there is to it? 

Well, yes, in part. 

But if you glance back, you may notice that it is not at all obvious. The ultrafilter construction is a necessary complication, and this complication partly explains why the hyperreals was not built earlier. Whether or not you like this construction is of course a subjective matter. Currently, the main advantage of non-standard analysis, is that it allows you to think *differently* about calculus. 

Instead of thinking about a process where finite elements shrink to zero, the hyperreals allow for a direct construction. In essence it makes it easier to extend properties of finite systems into continuous cases.

Let me note that there exists many other approaches to non-standard analysis: axiomatic, like [Internal Set Theory](https://en.wikipedia.org/wiki/Internal_set_theory) or [Alternative Set Theory](https://en.wikipedia.org/wiki/Alternative_set_theory), as well as constructionist, like the [surreal numbers](https://en.wikipedia.org/wiki/Surreal_number) or the [superreal numbers](https://en.wikipedia.org/wiki/Superreal_number).

## How to use it?

We now leave the safe shore of pretended rigor and jump into computation. We will do so with two simple examples, but first we need:

> **The transfer principle**
>
> Any appropriately formulated statement is true of $∗\mathbb{R}$, if and only if it is true of $\mathbb{R}$.

This principle is a necessity in non-standard analysis. For the ultrapower construction of the hyperreals&mdash;which we have considered here&mdash;the principle follows from [Łoś's theorem](https://en.wikipedia.org/wiki/Ultraproduct#.C5.81o.C5.9B.27s_theorem).

In order to transfer our results from the hyperreals and back to the reals, we define the *shadow*, $\mathrm{sh}(r)$, which maps a hyperreal number onto its closets real number. The function effectively removes any stray infinitesimals or infinites. We may do all our work within the hyperreals, and only return to the reals at the very end of our computation.

### The derivative

We start simple. Assuming&mdash;somewhat haphazardly&mdash;that simple functions may easily be transferred to the hyperreals, we define the derivative of a function as the shadow, 

$$ f'(x) = \mathrm{sh}\left(\frac{*f(*x + \epsilon) - *f(*x)}{\epsilon}\right), $$

where $\epsilon$ is a hyperreal infinitesimal. We now drop the star extensions for brevity. 

Take the cubic function, $f(x) = x^3$. The non-standard derivation follows then almost automatically:

$$ f'(x) = \mathrm{sh} \left( \frac{(x + \epsilon)^3 - x^3}{\epsilon} \right) = \mathrm{sh} \left( \frac{x^3 + 3 x \epsilon^2 + 3 x^2 \epsilon + \epsilon^3 - x^3}{\epsilon} \right). $$

Canceling terms and performing the overall division gives the well-known result,

$$ f'(x) = \mathrm{sh} \left( 3 x^2 + 3 x \epsilon \right) = 3 x^2. $$

### The intermediate value theorem

In order to contrast the standard epsilon-delta approach with our novel non-standard method we turn to the proof of the intermediate value theorem (also known as Bolzanos theorem). If you want to, you can take a look at [the standard proof](https://en.wikipedia.org/wiki/Intermediate_value_theorem#Proof) before continuing. 

The theorem considers a continuous function $f$ on the interval $[a, b]$. It states that for any $d$ in between $f(a)$ and $f(b)$, there exists $c \in [a,b]$ such that $f(c) = d$.

Without loss of generality we assume that $f(a) < f(b)$. Initially, we divide the interval $[a,b]$ into an integer, $N$, number of pieces of equal length, $\delta_N = (b-a)/N$. Consider now the first division point, $s_N$, where $f(s_N) > d$. Then logically $f(s_N - \Delta_N) \leq d$.

Consider the division of the interval into a number of segments given by the unlimited hyperinteger, $M \in \*\mathbb{N}$. Due to the transfer principle there still exists a smallest division point, $s_M$, where $f(s_M) > d$. However, $\Delta_M$ is infinitesimal, and this shows that $s_M \simeq s_M - \Delta_M$. By continuity $f(s_M) \simeq f(s_M - \Delta_M) \simeq d$. So the real number we are looking for is actually $c = \mathrm{sh}(s_M)$. Q.E.D.

This proof also ends this short section on the application of the hyperreals. As a side-note we introduced continuity on the hyperreals as $r \simeq s \Rightarrow f(r) \simeq f(s)$. If you are interested in a rigorous derivation, you can find it in the source material.

<!-- ### Distributions

The hyperreals allow for a direct construction of distributions as hyperreal functions. 

### Mathematical Physics

The Feynman Path Integral.
http://scitation.aip.org/content/aip/journal/jmp/47/9/10.1063/1.2339017
 
 -->

## Sources

I am indebted to the well-written article ["Infinitesimals: History & Application" by Joel A. Tropp](http://users.cms.caltech.edu/~jtropp/papers/Tro99-Infinitesimals.pdf). If you want to delve further into nonstandard analysis, you should give it a good read.

Also the textbook ["Elementary Calculus: An Infinitesimal Approach" by H. Jerome Keisler](http://www.math.wisc.edu/~keisler/calc.html) provided a sound foundation for my understanding of the hyperreals.

Wikipedia also has several articles about non-standard analysis, although I'd rather recommend the two sources above for further study.

I hope you have enjoyed this small excursion into the hyperreals. Now, at least you have an answer ready when pesky mathematicians question your logic. I have also read that people are working on applying non-standard reasoning to distributions and to concepts in mathematical physics like the Feynman Path-integral. I may (or may not) cover that in a later post&hellip;
