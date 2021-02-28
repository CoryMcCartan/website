---
title: "Northern Irish Parliamentary Constituencies"
description: 'How sectarian divisions translate to "independent and impartial" constituency boundaries'
summary: >
    In a place where religious polarization is stronger than political 
    polarization (though they are intertwined), how does the redistricting 
    process look? Are the boundaries fair? Random simulations can provide an
    answer.
date: 2021-02-28
output: 
    md_document:
        preserve_yaml: true
slug: northern-ireland
images:
    - ./2021/02/northern-ireland/cover.png
---

<span class="leadin">Redistricting is getting a lot of attention</span>
as the Census wraps up its data processing and we head into the 2021
redistricting cycle. And with good reason—between the [gutting of the
Voting Rights
Act](https://www.theguardian.com/us-news/2020/jun/25/shelby-county-anniversary-voting-rights-act-consequences),
[pandemic-related data
delays](https://www.ncsl.org/research/redistricting/2020-census-delays-and-the-impact-on-redistricting-637261879.aspx),
and ever-increasing partisanship, this will be an incredibly important
redistricting cycle.

But after doing a lot of work on redistricting in the U.S., I thought
I’d take a look at what goes on across the pond—in Northern Ireland,
specifically. In a place where religious polarization is stronger than
political polarization (though they are intertwined), how does the
redistricting process look? Are the boundaries fair?

# A Small Country, Divided

Northern Ireland consists of six of Ireland’s 32 counties, which were
partitioned from the rest of the island as part of the Irish
independence process. The Belfast metropolitan area, lying along the
Down–Antrim border, contains nearly a third of the country’s population.

<figure class="w6in">
<img src="figures/county-map-1.png" width="576" />
</figure>

Overall, 37% of households identify as Catholic and 44% identify as
Protestant, with an increasing number not identifying as religious. The
geographic distribution of Catholics and Protestants is complex, to say
the least. In Belfast, almost completely polarized wedges radiate
outwards in a kind of pinwheel pattern from the city center.

<figure class="w100">
<img src="figures/relig-map-1.png" width="768" />
</figure>

# Parliamentary Constituencies

Currently, Northern Ireland has 18 of the 650 seats in the Parliament of
the UK. The boundaries for these parliamentary constituencies, which are
also used to elect representatives to the Northern Ireland Assembly (5
representatives per constituency), were [slated to be replaced in 2019
following the final recommendations of a review process that ended in
2018](https://en.wikipedia.org/wiki/Sixth_Periodic_Review_of_Westminster_constituencies#Provisional_recommendations_(2018_review)),
but these new constituency boundaries were not adopted. A new review
will occur in 2023. Reviews are overseen by Boundary Commissions which
are [“independent and
impartial”](https://www.boundarycommission.org.uk/).

<figure class="w7in">
<img src="figures/current-relig-pop-1.png" width="672" />
</figure>

The constituencies are made up of statistical areas called “Super Output
Areas” (SOAs), and generally follow county boundaries. Ideally, they
would all have the same population, but as the figure above shows (using
2011 population counts), they don’t.

<figure class="w6in">
<img src="figures/current-map-1.png" width="576" />
</figure>

# How the Constituencies Measure Up

How do we go about determining the fairness of a set of parliamentary
constituencies? Simple measures, like comparing the fraction of
Catholics in the general population to the fraction of constituencies
which are plurality-Catholic, are tempting to use but ultimately
inadequate. The spatial distribution of voters can heavily skew these
kinds of numbers. For instance, it is nearly impossible to draw nine
congressional districts for the state of Massachusetts which result in a
single Republican seat, despite Donald Trump winning nearly a third of
the statewide vote. Is this unfair? Not under our first-past-the-post
electoral system. It’s just a consequence of Democrats being spread
fairly evenly across the state (compared to other states, at least).

So what’s the alternative? The state-of-the-art is to randomly generate
a bunch of other, hypothetical, sets of constituencies (“redistricting
plans”). Such a collection of random plans can form a baseline against
which to measure the actual, adopted plan. If the baseline is
constructed according to the proper legal standards, and the adopted
plan is significantly different from it, that’s evidence that the
adopted plan is unfair or possibly gerrymandered.

Generating these random plans is not straightforward, as there are
vastly more ways to draw redistricting plans than there are atoms in the
universe, and yet only a minuscule fraction of these plans satisfy all
the relevant legal constraints.

Here, we’ll use [a new
algorithm](https://imai.fas.harvard.edu/research/SMCredist.html) I’ve
developed expressly for this purpose, and we’ll enforce the following
constraints:

-   Each constituency should have a voting-age population within 5% of
    the ideal (which would be perfect equality; 76,672 people). This is
    required by law.
-   Each constituency should be geographically compact.
-   Each constituency should, to the greatest extent possible, follow
    county lines.

The Boundary Commission may also take into account historical
constituency boundaries and the boundaries of local wards. For the time
being, we’ll ignore these other considerations.

When we generate 1,000 random plans according to these constraints, we
get hypothetical plans that look like this:

<figure class="w7in">
<img src="figures/ex-plans-1.png" width="672" />
</figure>

For each plan, we can tally up the number of Protestants and Catholics
in each constituency, and sort the constituencies by these numbers.
Maybe one constituency is 85% Catholic, the next one is 81%, and so on
down to the least Catholic constituency, which might be 83% Protestant.
(For these comparisons, we look at the Catholic/Protestant fractions
among voters that identify one way or another; that is, we exclude minor
religions and the nonreligious.)

We take this set of numbers—the Catholic fraction in each constituency,
across the 1,000 random plans—and plot them on the graph below. Every
dot is a constituency taken from one of the simulated plans, and the
constituencies are arranged by how Catholic they are. Orange dots are
plurality-Protestant, and blue dots are plurality-Catholic. We see that
on average, across all these hypothetical plans, the most Catholic
constituency is usually around 76% Catholic.

<figure class="w100">
<img src="figures/distr-cath-county-1.png" width="768" />
</figure>

We also mark the fraction of Catholics in the current constituencies
with black lines. If this line falls below its corresponding set of
points, that means that that constituency has fewer Catholics than would
be expected based on our baseline of randomly generated plans.

The pattern here is one of polarization. Compared to neutrally-drawn
random plans, the existing constituencies have fewer Catholics in the
plurality-Protestant constituencies and fewer Protestants in the
plurality-Catholic constituencies, while the constituencies in the
middle are about average. Voters in each religious community are packed
in with similar voters, compared to what might otherwise be expected.
(Some polarization is expected of course, given the geographic
distribution of religions—that’s why the graph has an upward slope.)

Percentages are well and good, but how does this translate into seats?
Voting patterns in Northern Ireland are far from straightforward, with
several political parties that appeal to overlapping constituencies. But
it’s easy to convert the information in the above graph to a count of
the number of constituencies which are plurality Catholic and plurality
Protestant. Given the population numbers across the whole country, a
proportional breakdown would be 8 Catholic-plurality constituencies and
10 Protestant-plurality constituencies.

As the histogram below shows, that 8–18 split is indeed what should
happen on average, according to our baseline. But instead there’s a 7–17
split. At the same time, that isn’t too unusual—about 16% of the time,
we’d expect to see 7 or fewer plurality-Catholic constituencies.  
But it is one seat fewer than the average.

<figure class="w6in">
<img src="figures/cath-seats-county-1.png" width="576" />
</figure>

Why this discrepancy? Part of it could be population change since the
boundaries were last adjusted (in 2007, based on the 2001 census). And
the population has changed further since the 2011 census. But another
possible explanation lies in the Boundary Commission’s mandate to
consider the traditional boundaries of the constituencies.

We can explore this by generating another set of 1,000 baseline plans,
but adding one additional constraint: that the geographic “core” of each
constituency remain the same. What is the geographic “core”? For our
purposes, it will be the set of SOAs (the building blocks for
constituencies) which do not border another constituency. This means
that roughly 67% of voters are guaranteed to stay in the same
constituency. The effect of all of this is to create hypothetical plans
that are close to the existing boundaries.

The graph below is the same as the one as above, but uses this new
baseline. And the pattern above—that constituencies were more
religiously polarized than we would expect—mostly disappears.

<figure class="w100">
<img src="figures/distr-cath-cores-1.png" width="768" />
</figure>

Going from here requires less math and more philosophy. Is it a good
thing to have more religiously homogeneous constituencies? If not, are
the existing boundaries a religious gerrymander or just drawn to reflect
the old boundaries? How did those boundaries get to be the way they
were? How would we move towards more integration while respecting
traditional boundaries, anyway?

Conversely, if religious homogeneity is a good thing—after all, it tends
to reduce the number of wasted votes (Catholics in Protestant
constituencies, and vice versa)—how far can we push it? Is more
polarization possible?

There are [other redistricting
tools](https://www.sciencedirect.com/science/article/abs/pii/S2210650216300220)
that are better suited to answering questions like this, but we can gain
an idea of what’s possible by generating yet another set of baseline
simulations. This time, we’ll explicitly group together Catholic and
Protestant areas, so that these areas aren’t split by the redistricting
process.

The results of this simulation are shown in the graph below. While the
overall shape doesn’t show much more polarization than what is already
seen under the current boundaries, we now see a couple plans which yield
11 Catholic-plurality constituencies and only 7 Protestant-plurality
constituencies.  
Compared to a proportional split of 8–18, this is rather a lot, and we
don’t see the same possibility for more Protestant-plurality
constituencies beyond 12.

<figure class="w100">
<img src="figures/distr-cath-gerry-1.png" width="768" />
</figure>

One of these 11–7 split plans is shown below. The general strategy is to
merge Belfast East and Belfast South, while adjusting the boundaries of
Belfast West and mopping up the remains with Belfast North. Upper Bann
and Lagan Valley are shifted northwards, adding enough Catholics to tip
them into a Catholic plurality. With the leftover constituency created
by merging Belfast East and South, the constituency of South Down, a
Catholic stronghold, can be split into two more closely divided
constituencies that cover the areas left by Upper Bann and Lagan Valley.

<figure class="w6in">
<img src="figures/catholic-gerry-1.png" width="576" />
</figure>

An interesting exercise, for sure. But voting patterns and ultimate
constituency winners are not so easily predicted from religious
affiliation alone. Not to mention that Sinn Féin MPs don’t take their
seats in Parliament anyway.
