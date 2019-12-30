---
title: "37 Supreme Court Justices on a Plane"
description: "Two-dimensional ideal points using multidimensional scaling"
date: 2017-10-26
---

The most common measure of Supreme Court justice ideology are the 
[Martin--Quinn scores](https://mqscores.lsa.umich.edu/), developed by the
eponymous political scientists.  Since their [original publication in
2002](https://mqscores.lsa.umich.edu/media/pa02.pdf), the scores have been
widely used, in political science and in the media, to place justices on
a left--right political spectrum.<!--more-->

The scores are parameters in a Bayesian item-response model. These types of 
models originated in education research but have since been used to analyze
legislatures and courts in the U.S. and around the globe.  While there is
much to like about these Bayesian models, they are computationally intensive,
as they involve the estimation of hundreds, if not thousands, of parameters
which are related by a nontrivial dependence structure.  

Similar left--right scores, viewed as an approximation the Martin--Quinn scores,
may be generated through a technique called [multidimensional
scaling](https://en.wikipedia.org/wiki/Multidimensional_scaling), or MDS. One
advantage of this approach, other than computational efficiency, is that it
naturally generalizes to higher dimensions. MDS tries to find coordinates
_n_-dimensional Euclidean space such that the pairwise distance between points
matches that of a user-provided distance matrix.  As this matrix is often 
much larger than the desired dimensionality of the MDS output, no perfect
solution exists; MDS rather minimizes some loss function over the realized
distance matrix (the details vary by flavor of MDS).

The figure below shows the approximate Martin--Quinn scores estimated by
one-dimensional MDS. Positive scores reflect conservatism. The general leftward
trend for individual justices is clear. Justices are colored by the seat on
the court that they occupy; the chief justice is colored in black.

{{< figure src="/images/court-old/scores_1d.png" class="w100" >}}

Many Supreme Court justices reject the notion that they fit neatly on a
political spectrum, pointing to cases where the Court divided along lines that
cannot be explained by left-right ideology.  Other Court observers have
suggested that a second dimension along which justices may be measured is that
of pragmatism: how willing are justices to adapt the law to fit practical
necessities, versus holding an ideologically consistent line?

The two-dimensional MDS scores, illustrated below, suggest that this dimension
may indeed be important. While the scores are less stable (retroactive smoothing
had to be applied to stabilize the MDS estimates), and harder to visualize (dots
on each justice trajectory show the justices' ending positions; retired justices
are partially greyed out), the second dimension (the vertical axis) does seem
to partially capture the pragmatic/idealist divide.  Justices like Samuel Alito
and Stephen Breyer, viewed as some of the more pragmatic justices on the
current Court, have higher second-dimension scores than Antonin Scalia, for
example.

{{< figure src="/images/court-old/scores_2d.png" class="w100" >}}

Hopefully in the future we can fit a full Bayesian item-response model
to better (and more stably) estimate these two-dimensional scores.
