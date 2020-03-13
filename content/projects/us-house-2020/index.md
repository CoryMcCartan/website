---
title: 2020 House Forecast
description: Will Democrats maintain their majority?
date: 2020-03-11
slug: us-house-20
images:
    - /election-2020/capitol.jpg
js: ["https://d3js.org/d3.v5.min.js"]
css: ["/projects/us-house-20/graphics.css"]
---

<div id="chart_hist"></div>

<section id="histogram" class="graphic"></section>
<section class="banner">
<span class="text"></span>
<span class="updated"></span>
</section>

<h1>What does a <span id="prob_win"></span> chance feel like?</h1>
Click the button below to randomly simulate a hypothetical election. While
the Democrats may <span id="dem_neg"></span>be favored to win, there's a lot of
variation in how many seats they may gain or lose.

<p><div style="display: flex; flex-wrap: wrap;">
<button id="sim_elec">Simulate an election</button>
<div id="sim_result"></div>
</div></p>

# How the odds have changed
The model works by using economic indicators, structural factors (like whether 
it is a midterm year, or the party that controls the White House), and 
[national polling data](#national-polling) to estimate what the nationwide 
popular vote (adding up all the votes for each party in all 435 districts) and
the seat breakdown will be.

Of course, there is a lot of uncertainty in elections and polling. The model
takes this into account, combining uncertainty across all of these factors
to arrive at an overall distribution of the number of seats that the Democrats
will win. From this distribution, we can figure out the chances that the
Democrats win at least 218 seats and keep their majority.

The model is updated regularly as new economic and polling data come in. The
charts below show how the forecast has evolved over time.

<section id="prob_history"></section>

The Democrats have a <b id="prob_win2"></b> chance of winning a majority,
but only a <b id="prob_gain"></b> chance of winning more seats than the 255
they won last election. The chart below shows the estimated range of Democratic
seats, and how it has changed over time.  The range will narrow as we approach
the election, because we will have more information, and there will be less time
for the race to be upended by an economic or political development.

The outer band below is an **90% credible interval**, meaning that based on the
information available at the time the forecast was made, there was an 90%
chance that the Democrats would win a number of seats somewhere in that
interval. The inner band shows a **50% credible interval**.

<section id="seat_history"></section>

# National Polling
The best predictor of the House race, and the one that has the potential to
change the most between now and November is the so-called "generic ballot," 
where polling firms ask voters which party they plan on voting for in their
local House race.

Since November 2019, <b id="n_polls"></b> generic ballot polls have been
conducted.  As new polling data arrive, the model re-estimates how the
Democratic share on the generic ballot has evolved over time, and forecasts how
it could change toward Election Day. The model makes an initial guess of the
Election-Day popular vote based on the structural and economic factors
mentioned above.  Right now, it estimates that the Democrats have a
<b id="prob_pop"></b> chance of winning the popular vote.

<section id="public_opinion"></section>

In estimating the popular vote from polling data, the model also takes into 
account the tendency of certain kinds of polls to over- or under-estimate the
support for each party. For example, polls of likely voters are generally
more accurate than polls of all registered voters, and the latter tend to lean
more Democratic.

In addition, certain polling firms have a pattern of producing polls that lean
toward one party or another.  These "house effects" are estimated by the model
and used to make adjustments in estimating overall public opinion.  Negative
house effects (red) mean that the firm's polls overestimate Republican support;
positive effects (blue) mean that the firm overestimates Democratic support.

<table id="firms">
<col width="42%">
<col width="8%">
<col width="25%">
<col width="25%">
<tr><th>Firm</th><th>Polls</th><th colspan="2">House Effect</th></tr>
</table>

<div style="height: 5em; border-bottom: 1px solid #777;"></div>

### Methodology

<div class="details">

The "model" is actually three separate models: a prior model for public opinion,
a voter intent model for polling data, and a results model for the number of 
seats won by each party.

The prior model is a linear model which predicts the House popular vote on
Election Day (on a logit scale) based on the president's approval rating,
earnings growth, GDP growth, the unemployment rate, which party controls the
White House, and whether or not it is a midterm election (along with some
interaction terms). The model uses House elections since 1974 to make its
predictions.

The voter intent model predicts the true state of public opinion at every
week of the race, up to and including Election Day. The main parameter of
interest is latent support for the Democratic party (on a logit scale). The 
results of each poll are assumed to be drawn from a binomial distribution
with this latent probability, adjusted for the polling firm's house effects,
the type of respondents (registered voters, likely voters, or all adults), 
poll-specific error, and national polling error. Each of these adjustments is
a parameter that the model estimates. National polling error cannot be
estimated from polling data, and essentially just adds noise to the model. Its
distribution is estimated from past elections' polling errors.

Latent voter intent is assumed to follow a random walk from week to week, with
Gaussian increments. The prior model sets a distribution of the walk on Election
Day, and the walk then evolves backward in time. It is this backward evolution
of the walk, combined with the Election Day prior, which keeps the variance of
the public opinion estimates from growing linearly from the present day.

The results model is a linear model which predicts the number of Democratic
seats won based on the seats won in the previous election, the share of
the national popular vote won by the Democrats, which party controls the House
and the presidency currently, and whether it is a midterm election (along with
some interaction terms). Like the prior model, the results model uses House
elections since 1974 to make its predictions.

Both linear models use Cauchy(0, 1) priors on the coefficients of centered and
scaled predictors. Models were fit using [STAN](https://mc-stan.org). Model code 
and data are [available online](https://github.com/CoryMcCartan/us-house-20).

</div>

<script src="charts.js"></script>
<script src="main.js"></script>
<style>
</style>
