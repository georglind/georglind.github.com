---
layout: post
title: "Non-standard Analysis"
date: 2015-11-12 09:00
comments: True
categories: [Mathematics, Education]
---

Physicists! We deal with mathematics on a needs come, needs serve basis. We regularly divide with infinitesimals, exchange the order of integration and differentiation, sum part of an infinite series. Rigor is dead and buried as long as we end up with meaningful and useful answers!

The road to becoming a theoretical physics include numerous math courses: Algebra, Measure theory, Geometry, and&hellip; Analysis. The mathematical analysis courses investigate mathematical functions, derivatives and integration, and in doing so need to deal with the infinitely small. 

Historically, the idea of taking from something small but finite to the infinitely small, has been employed by many mathematicians throughout the ages, including [Archimedes](https://en.wikipedia.org/wiki/The_Method_of_Mechanical_Theorems), [Fermat](https://en.wikipedia.org/wiki/Adequality), [Euler](https://en.wikipedia.org/wiki/Introductio_in_analysin_infinitorum), Bolzano, and Cauchy. Its greatest achievement was the development of calculus, where Newton and Leibniz introduced positive quantities smaller than any real number and called them "fluxions" or "inifinitesimals". 

It was those infinitesimals, which made serious formalistic mathematicians, like David Hilbert, uneasy. Infinity is not even part of the real numbers, and infinitesimals are certainly *not.* So, how can we do calculations with numbers that do not exist? It was Karl Weierstrass, who in the end followed up on the work of [Bolzano](https://en.wikipedia.org/wiki/Bernard_Bolzano#Mathematics). He got completely away with the infinitesimals and instead introduced the concept of limits, and the method of epsilon-delta reasoning.

Weierstrass performed a great feat, which is currently being celebrated in every calculus textbook, and in many course Analysis-101 courses. However, I'm sure that most people have felt that this rigid approach to calculus could not be the full story. How could a successful tool like calculus have been built on such a shaky ground? And then stood there majestically for centuries until somebody eventually took the time to secure the foundations? 

[Abraham Robinson](https://en.wikipedia.org/wiki/Abraham_Robinson) was the first to seriously consider taking infinitesimals seriously. He expanded the field of real numbers by including unlimited numbers and the infinitesimal numbers. This expansion is known as the *field of hyperreals*, and we are going to take a close look at it, based on the most common construction from something called *ultrafilters*.

## Ultrafilters

In order to construct the hyperreals, the concept of *ultrafilters* will come in handy. And **no**, I have no idea why they are called ultrafilters&hellip;

{% img center /files/nonstandard_analysis/ultrafilter.png 'Ultrafilter' 'Ultrafilter' %}

No matter&hellip; A free ultrafilter $U$ on the natural numbers, $\mathbb{N}$, is a set of subsets of $\mathbb{N}$ with the properties that,

1. $U$ only contains infinite subsets of $\mathbb{N}$.
2. For two elements in $U$ (let us call them $X\_1$ and $X\_2$), the intersection of those two sets must also belong to $U$, so $X\_1 \cap X\_2 \in U$.
3. Consider some infinite subset $X\_1$ which belongs to $U$. All supersets of $X\_1$ (all $X\_2 \supset X\_1$) then also belongs to this ultrafilter.
4. If $X \notin U$ then the complement of $X$ \(written as $\mathbb{N} \setminus X$\) belongs to $U$. 

As a simple example consider the empty set $\emptyset = \\{\\}$. The empty set is finite and hence, it does *not* belong in an ultrafilter (per statement 1). The complement of the empty set (which is the full set $\mathbb{N} \setminus \emptyset = \mathbb{N}$) then instead belongs to $U$ (per statement 4).

On the other hand: Consider the infinite subset containing all the even numbers, $\mathbb{N}_e$, and the subset containing all the odd numbers, $\mathbb{N}_o$. The intersection of those two subsets $\mathbb{N}_e \cap \mathbb{N}_o = \emptyset$, and hence they cannot both belong to our ultrafilter (per statement 2). Because the two sets are the complements of each other, exactly *one* of them must belong to $U$ (per statement 4), but we are free to choose which one!

So the ultrafilter is not unique, but it can be shown that two ultrafilters on the same set are equivalent, and one can be constructed from the other simply by exchanging some elements with their complements.

## The hyperreals

After this small intermission, we are ready to construct the hyperreals. This particular construction is based on sequences. A sequence is a function on the positive integers, and it is generally written as,

$$ \underline{a} = (a_1, a_2, a_3, \ldots) = \big( a_j \big)_{j=1}^\infty = ( a_j ) $$

Here the hyperreals are constructed from infinite sequences on the reals, $\underline{a} \in \mathbb{R}^{\mathbb{N}}$. The real numbers themselves can easily be represented as infinite sequences with constant elements,

$$ \underline{x} = (x) = (x, x, x, \ldots). $$

So the number,

$$ (2) = (2, 2, 2, \ldots) $$

However we may dream up many other sequences, like these: 

$$ (0, 1, 0, 1, 0, \ldots) \text{ or } (1, 2, 3, 4, 5, 6, \ldots).$$

Like the real numbers we we want the hyperreal numbers to be ordered, so any two numbers are either smaller or larger than each other. The main problem with sequences is that they cannot be compared to each other in a consistent way! In order to extract something usable, we must "thin out" the forest of possible sequences.

The idea, which help us overcome this obstacle, is to let two sequences represent the same hyperreal number if "most" of their elements are identical. For a consistent definition of "most" we return to the ultrafilter construction. In general we will say that two sequences are equivalent, $\underline{r} \equiv \underline{s}$, if and only if the places, at which they share elements, form an infinite set that belongs to our ultrafilter, $U$:

$$\langle r = s \rangle = \{j \in \mathbb{N}: r_j = s_j\} \in U.$$

Using the properties of the ultrafilter, it is easy to show that this construction is transitive and hence defines an equivalence relation. The resulting equivalence classes defines the *hyperreals*:

$$ *\mathbb{R} = \{ [r] \, : \, r \in \mathbb{R}^\mathbb{N} \} $$

Hyperreal numbers may be manipulated by first choosing sample sequences from the relevant equivalence classes, then performing element-wise operations on those sample sequences, and finally representing the resulting hyperreal as the equivalence class of the resulting sequence. Addition and multiplication are then directly defined as,

$$ r \oplus s =  [r] + [s] = [(r_j + s_j)]$$

$$ r \odot s = [r] \cdot [s] = [(r_j \cdot s_j)] $$

We are now ready to shoe that this careful construction allow us to order the hyperreals. Assume that one sequence, $r$, for "a large part" is smaller than another sequence, $s$. Again we take "for a large part" to mean that the sequence indices at which $r$ is smaller than $s$ belong to our ultrafilter, so $\langle r < s \rangle =  \\{ j : r_j < s_j \\} \in U$. It follows almost automatically that $r \not\equiv s$, because $\langle r = s \rangle \subset \mathbb{N} \setminus \langle r < s \rangle \not\in U$ (by use of ultrafilter property 1 and 4). 

When applied a little more rigorously this shows that the hyperreals, $(*\mathbb{R}, \oplus, \odot)$, indeed form an ordered field.

### The reals

As we already anticipated, the real numbers are embedded in the hyperreals, and are now represented classes equivalent to the constant sequences. We introduce a map from the reals to the hyperreals, $* : \mathbb{R} \rightarrow *\mathbb{R}$, such that

$$ *x = [\underline{x}] = [(x, x, x, \ldots)] $$

And we will refer to these hyperreal numbers as *standard*. This directly equips the hyperreals with neutral elements for addition, $\*0$, and multiplication, $\*1$.

You may also remember this alternating sequences that we looked at earlier:

$$ (0, 1, 0, 1, 0, 1, \ldots ),$$

It directly shows the cleverness of the ultrafilter construction. This sequence overlaps with the real number $\*0$ on all the even sites, and with the real $\*1$ on all the odd sites. From our discussion of ultrafilters, we know that the set of even numbers, $\mathbb{N}_e$, and the set of odd numbers, $\mathbb{N}_o$ *cannot* belong to the same ultrafilter. This means that for some choice of ultrafilter, the alternating sequence will belong to the $\*0$ equivalence class, and in others it may belong to the $\*1$ class.

### Infinitesimals

The hyperreals also contain a lot of numbers in the vicinity of the standard numbers. Consider for example the hyperreal $s = [\underline{s}]$ defined by the sequence,

$$ \underline{s} = (r + 1/j)_{j=1}^\infty $$

This sequence only intersects sample sequences from the standard number classes a *finite* number of times. This makes the corresponding hyperreal number, $s = [\underline{s}]$, decidedly *non-standard*. It is easy to show that $\langle *x < s \rangle = \mathbb{N}$. More interestingly $s$ squeezes in between $\*x$ and any other standard number $y > x$, because $\langle s < y \rangle \in U$. 

The difference between those two hyperreal numbers, $s - \*x$, is now smaller than any positive real number, and we may refer to it as *infinitesimal*. Note that there exist a whole plethora of well-ordered infinitesimals, such that we may say that one is larger than the other and vice versa. When two hyperreal numbers, $s$ and $r$, are separated by an infinitesimal, we write that $s \simeq r$. 

We can then introduce two useful functions. First comes the *halo* of a given hyperreal, 

$$\mathrm{hal}(r) = \{ s \in *\mathbb{R} : s \simeq r\} $$

Similarly, we say that two hyperreals, $s$ and $r$, are limited separated whenever their distance is *not* an infinitesimal, and we write $s \sim r$. The classes of this equivalence relation are called the *galaxies*, and we write.

$$\mathrm{gal}(r) = \{ s \in *\mathbb{R} : s \sim r \} $$

We may take a look at the hyperreal infinitesimals. We can do this by looking through the *infinitesimal microscope*&mdash;a pedagogical representation of the hyperreal number line originally introduced by Jerome Keisler. Focusing on a particular hyperreal, $r$, the microscope magnifies its halo:

{% img center /files/nonstandard_analysis/microscope-01.png 'The infinitesimal microscope' 'The infinitesimal microscope' %}

### Unlimited numbers

The unlimited numbers form another interesting family of hyperreal numbers. Consider for example the hyperreal number represented by,

$$ n = [\underline{n}] = [(1, 2, 3, 4, 5, \ldots )]. $$

It is clearly non-standard (its sample sequences only overlap real number sequences at a finite number of places), and it is also greater than any real number: All properties which we normally associate with the infinite. However, like the infinitesimals, there are many different unlimited numbers within the hyperreals. Consider for example:

$$ m = [\underline{m}] = [(2, 3, 4, 5, 6, \ldots)]. $$

Here $m$ is also infinite, and in addition $m > n$, which may confuse or comfort you, depending on your mathematical standpoint.

## Hey, wait a minute...

What have we just done? It seams that we have taken the [Cauchy sequences](https://en.wikipedia.org/wiki/Cauchy_sequence) and turned those sequences into numbers themselves... or entities? Is that all there is to it? 

Well, yes, in part. 

If you reread the above explanation you will notice that is was no easy feat. We had construct a complicated concept in order to come up with a workable version of the hyperreals. Whether or not you like this construction is of course a subjective matter. Currently the main advantage of non-standard analysis seems to be that it allow you to *think* differently about calculus. 

Instead of thinking about a process where finite elements shrink to zero, the hyperreals allow for a direct construction. In essence it makes it easier to extend properties of finite systems into continuous cases.

Let me note that there exists many other approaches to non-standard analysis: axiomatic, like [Internal Set Theory](https://en.wikipedia.org/wiki/Internal_set_theory) or [Alternative Set Theory](https://en.wikipedia.org/wiki/Alternative_set_theory), as well as constructionist, like the [surreal numbers](https://en.wikipedia.org/wiki/Surreal_number) or the [superreal numbers](https://en.wikipedia.org/wiki/Superreal_number).

## How to use it?

We will now leave the safe shore of pretended rigor and simply jump into computation. We will do so with two simple examples, but first we will need:

> **The transfer principle**
>
> Any appropriately formulated statement is true of $∗\mathbb{R}$, if and only if it is true of $\mathbb{R}$.

This principle is a necessity in non-standard analysis. For the ultrapower construction of the hyperreals&mdash;which we have considered here&mdash;the principle follows from [Łoś's theorem](https://en.wikipedia.org/wiki/Ultraproduct#.C5.81o.C5.9B.27s_theorem).

In order to transfer our results from the hyperreals and back to the reals, we define the *shadow* of a hyperreal number, $\mathrm{sh}(r)$, which maps the hyperreal number onto the closets real number. The function effectively removes any stray infinitesimals or infinites. Hence we may do all our work within the hyperreals, and only return to the reals at the very end of our computation.

Assuming, haphazardly, that simple functions may easily be transferred to the hyperreals, we define the derivative of a function, as the shadow, 

$$ f'(x) = \mathrm{sh}\left(\frac{*f(*x + \mathrm{d}x) - *f(*x)}{\mathrm{d}x}\right) $$

where $\mathrm{d}x$ is a hyperreal infinitesimal. As an example consider the cubic function, $f(x) = x^3$. The non-standard derivation follows then from (where we have dropped the star extensions which are necessary, but annoying to both read and write),

$$ f'(x) = \mathrm{sh} \left( \frac{(x + \mathrm{d}x)^3 - x^3}{\mathrm{d}x} \right) = \mathrm{sh} \left( \frac{x^3 + 3 x \mathrm{d}x^2 + 3 x^2 \mathrm{d}x + \mathrm{d}x^3 - x^3}{\mathrm{d}x} \right) $$

Then canceling terms and performing the overall division, produces the well-known result,

$$ f'(x) = \mathrm{sh} \left( 3 x^2 + 3 x \mathrm{d}x \right) = 3 x^2 $$

### The intermediate value theorem

The proof of the intermediate value theorem (Bolzano's theorem) takes on a simple form in non-standard analysis. The theorem considers a continuous function $f$ on the interval $[a, b]$. For any $d$ in between $f(a)$ and $f(b)$, there exists a $c \in [a,b]$ such that $f(c) = d$.

Without loss of generality we assume that $f(a) < f(b)$. Initially, we divide the interval $[a,b]$ into an integer, $N$, number of pieces of equal length, $\delta_N = (b-a)/N$. Consider now the first division point, $s_N$, where $f(s_N) > d$. Then $f(s_N - \Delta_N) \leq d$.

Then consider the division of the interval into a number of segments given by the unlimited hyperinteger, $M \in \*\mathbb{N}$. Due to the transfer principle there still exists a smallest division point, $s_M$, where $f(s_M) > d$. However, $\Delta_M$ is infinitesimal, and it is obviously true that $s_M \simeq s_M - \Delta_M$. By continuity $f(s_M) \simeq f(s_M - \Delta_M) \simeq d$. This means that we have found a real number $c \simeq s_M$. *qed*.

This proof ends our computations with the hyperreals. On the fly, we introduced continuity on the hyperreals as $r \simeq s \Rightarrow f(r) \simeq f(s)$. If you are interested in a rigorous derivation, you can find it in the source material for this small introduction.

<!-- ### Distributions

The hyperreals allow for a direct construction of distributions as hyperreal functions. 

### Mathematical Physics

The Feynman Path Integral.
http://scitation.aip.org/content/aip/journal/jmp/47/9/10.1063/1.2339017
 
 -->

## Sources

I am very much indebted to the well-written article ["Infinitesimals: History & Application" by Joel A. Tropp](http://users.cms.caltech.edu/~jtropp/papers/Tro99-Infinitesimals.pdf). If you want to delve further into nonstandard analysis, you really should give it a good read.

Also the textbook ["Elementary Calculus: An Infinitesimal Approach" by H. Jerome Keisler](http://www.math.wisc.edu/~keisler/calc.html) provided a sound foundation for understanding of the hyperreals.

Wikipedia also has several articles about non-standard analysis, although I'd rather recommend the two sources above for further study.

I hope you enjoyed this small excursion into the hyperreals. I know that people are working on applying non-standard reasoning to distributions and to mathematical physics like the Feynman Path-integral. I may (or may not) cover that in a later post&hellip;
