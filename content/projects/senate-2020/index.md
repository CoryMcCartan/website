---
title: 2020 Senate Forecast
description: >
    Can the GOP hold on to Senate control after six years in the majority?
date: 2020-06-06
slug: senate-20
featured: true
images:
    - /election-2020/capitol.jpg
js: [
    "https://d3js.org/d3.v5.min.js",
]
css: [
    "/projects/senate-20/graphics.css",
    "/election-2020/shared.css",
]
---

<div id="forecast-links" class="tabs">
<span>
<a href="/election-2020/" style="opacity: 0.7">2020 FORECASTS</a>
<img src="/election-2020/flag.gif" 
    style="height: 32px; margin: -8px 0 -11px 6px;">
</span>
<a href="/projects/president-20/">President</a>
<a href="/projects/senate-20/" class="current">Senate</a>
<a href="/projects/us-house-20/">House</a>
</div>


<section id="histogram"></section>

<section class="banner">
<span class="text"></span>
<span class="updated"></span>
</section>


# What does a <span id="prob_win"></span> chance feel like?

There is a wide range of possible outcomes across all 35 races.  Click the
button above to randomly simulate one possible election result. 

<div style="display: flex; flex-wrap: wrap;">
<button id="sim_elec">Simulate an election</button>
<div id="map_sim_result" class="sim_result"></div>
</div>


# How the odds have changed

The model works by first building a [structural forecast](#prior-model) for the
national race and the race in each state, based on economic indicators, the
president&rsquo;s approval rating, past election results, the home races of each of
the candidates, and incumbency and regional effects. 

The model then uses state and national polls to [estimate public
opinion](#national-polling) in every state and nationally, and makes a forecast
for Election Day by simulating thousands of possible elections, taking into
account the structural forecast based on the non-poll factors. 

Of course, there is a lot of uncertainty in elections and polling. The model
takes this into account, combining uncertainty across all of these factors to
arrive at an overall distribution of the number of seats that each party will
win. From this distribution, we can figure out the chances that the Democrats
and Republicans will win at least 50 seats (or 51, if they don&rsquo;t win the
presidency) and control the Senate.

The model is updated regularly as new economic and polling data come in. The
charts below show how the forecast has evolved over time.

<div id="history_tabs">
<div class="tabs">
<a href="#prob_history" class="current">Overall odds</a>
<a href="#seats_history">Seats</a>
<a href="#pv_history">Public opinion</a>
</div>

<section id="prob_history">
<div class="chart"></div>

This chart shows how the model&rsquo;s estimate of the overall probability of
winning the presidency has changed over time. Because the model is based on
random simulations, these probabilities will naturally jump around a bit, so a
shift of a few percentage points in either direction doesn&rsquo;t usually
reflect a change in the state of the race.

</section>

<section id="seats_history">
<div class="chart"></div>

This chart shows the estimated range of seats that the Democrats will
win, and how it has changed over time. 

The range will narrow as we approach the election, because we will have more
information, and there will be less time for the race to be upended by an
economic or political development.

The outer band above is an **90% credible interval**, meaning that based on the
information available at the time the forecast was made, there was an 90%
chance that the Democrats would win a number of seats somewhere in that
interval. The inner band shows a **50% credible interval**.
</section>

<section id="pv_history">
<div class="chart"></div>

This chart shows the estimated margin in the national generic ballot (see more
<a href="#national-polling">below</a>), and how it has changed over time.  The range will narrow
as we approach the election, because we will have more information, and there
will be less time for the race to be upended by an economic or political
development.

The outer band above is an **90% credible interval**, meaning that based on the
information available at the time the forecast was made, there was an 90%
chance that the Democrats would win a number of seats somewhere in that
interval. The inner band shows a **50% credible interval**.

</section>

</div>

# Race forecasts

The table below summarizes every Senate race, including the forecasted
vote share (excluding write-ins and third parties) and probability of winning.
Seats that are more likely than not to flip parties are highlighted in gray.
You can click on the column headers in order to sort the table, or click on a
race to see more details.

<table id="races" class="minim">
<col width="25%">
<col width="9%">
<col width="12%">
<col width="21%">
<col width="21%">
<col width="12%">

<thead>
<tr>
<th data-kind="race" data-asc="1">Race</th>
<th data-kind="inc" data-asc="1" class="small">Incumbent</th>
<th data-kind="prob" data-asc="0" class="small">Chances of winning</th>
<th data-kind="vote" data-asc="0" colspan="2">
Estimated vote share
<div style="font-weight: 300; color: #666; font-size: 0.85em; margin-top: 2px; line-height: 1;">
Bands show 50% and 90% credible intervals</div>
</th>
<th data-kind="margin" data-asc="1">Margin</th>
</tr>
</thead>

<tbody></tbody>
</table>

<div style="display: flex; justify-content: space-around; margin-bottom: 2em;">
<button id="show">Show more races</button>
</div>


Select a race to see detailed forecasts and how they&rsquo;ve changed over time.

<select id="race">
</select>

<span id="selected_race"></span><span id="race_inc"></span>.
<span id="race_polls"></span>

<section id="race_history"></section>


# Possible scenarios

There is a <b id="prob_tie"></b> chance of a 50-50 tie in the Senate,
in which case control is decided by the party that wins the Vice Presidency.
Our <a href="/projects/president-20/">presidential model</a> gives the Democrats
a <b id="prob_pres"></b> chance of winning the presidency.

The two charts below show the forecasted distribution of Democratic and
Republican seat gains, and how they&rsquo;ve changed over time. While the 
Democrats are currently only strongly favored to pick up a few seats, as the
table above shows, there are many more races in which they have a
medium-to-long shot than the Republicans, whose only best pickup opportunity
after than Alabama is New Mexico.

<section id="pickup_history"></section>

### What happens if&hellip; ?

There are many paths to a Senate majority. No one race is absolutely critical
for a party to win. But races&rsquo; outcomes are correlated with one another, and
winning one race can be a sign of strength elsewhere. 

The buttons below are for the twelve closest races.  Click them to cycle
through hypothetical winners and play out different scenarios. What if the
Democrats win Maine but the G.O.P. wins Alabama?  You could even use these
buttons on election night to provide live estimates of the race as each state
is called.

<div id="race_buttons"></div>
<a id="reset_races">Reset all</a>

<div id="filter_warning" class="sim_result"></div>
<div id="filter_sum" class="sim_result"></div>
<div id="filter_prob"></div>
<div id="scenario_prob" style="color: #666; margin-top: 0.25em;"></div>


# Model components

The model works by combining various structural, non-polling factors with state
and national polls to arrive at an overall forecast for the election. The
sections below provide more detail on each of these components.

### Prior model

One of the best predictors of the national Senate race, a is the so-called
“generic ballot,” where polling firms ask voters which party they plan on
voting for in their local House race.

The first component of the model is a so-called "prior" guess about what this
generic ballot will be on Election Day.  This prior model uses the president&rsquo;s
approval rating, earnings growth, GDP growth, the unemployment rate, which
party controls the White House, and whether or not it is a midterm election to
create a forecast of <b id="natl_prior"></b> for the Democrats.

The second part of the model is a prior guess about how the vote in each
race will differ from the national vote.  The best predictor of this 
differential is the results in the last election, but the model also incorporates
the average partisan lean (from presidential election results), and adjusts for
incumbency effects, for both the individual candidate and his or her party.

### National polling

With the initial prior guesses in hand, the model then combines them with 
polling data to arrive at an election-day forecast.

Support for the candidates in polls now is obviously not necessarily the same
as their vote share on Election Day. The model adjusts and averages polls to
estimate public opinion for each 3-day period of the race up to the present
day, and then forecasts how it will change toward November. 

Since mid--January, <b id="n_polls"></b> polls have been conducted. Polls
conducted early on in the race (especially national polls) don&rsquo;t have much
impact on the overall forecast, since voters&rsquo; opinions will change a lot
before November. But as we get closer to Election Day, the polls become more
informative about the final result.

The chart below shows the model&rsquo;s estimates of voters&rsquo; margin of support for 
the parties for each point in the race. The rightmost values on this chart
are the election-day popular vote forecast.

<section id="public_opinion"></section>

In estimating the popular vote from polling data, the model also takes into 
account the tendency of certain kinds of polls to over- or under-estimate the
support for each party. For example, polls of likely voters are generally
more accurate than polls of all registered voters, and the latter tend to lean
more Democratic.

In addition, certain polling firms have a pattern of producing polls that lean
toward one party or another.  These "house effects" are estimated by the model
and used to make adjustments in estimating overall public opinion.  Negative
house effects (red) mean that the firm&rsquo;s polls overestimate Republican support;
positive effects (blue) mean that the firm overestimates Democratic support.

<table id="firms">
<col width="42%">
<col width="8%">
<col width="25%">
<col width="25%">
<thead>
<tr><th>Firm</th><th>Polls</th><th colspan="2">House Effect</th></tr>
</thead>
<tbody></tbody>
</table>

<div style="height: 5em; border-bottom: 1px solid #777;"></div>



### Methodology

<div class="details">

The structure of this model is the same as the [presidential model](/projects/president-20/).

The above [components section](#model-components) lays out the general overview
of the model. All submodels operate on the logit scale.  The prior models for the
national vote and state differentials are linear models (with random effects
for the state model); Cauchy(0, 2.5) priors on scaled and centered predictors
were used. 

The polling model is similar to a 2016 presidential election model by 
[Pierre-Antoine Kremp](https://www.slate.com/features/pkremp_forecast/report.html),
which in turn is built on Drew Linzer&rsquo;s [dynamic Bayesian forecasting 
model](https://votamatic.org/wp-content/uploads/2013/07/Linzer-JASA13.pdf).
In contrast to those models, this one incorporates a critical adjustment for
the bias of registered-voter and all-adult polls, uses past election data
to estimate polling errors, and uses more informative priors on national 
and race outcomes, built from the linear models described above.

Essentially, there is a latent national voter intent, and latent state
differentials (how much more or less Democratic the state is than the national
vote), which evolve as a random walk with Gaussian increments in 3-day and
3-week steps (the races&rsquo; walk has larger steps for computational reasons).
The national and race priors become priors on the final step of the random
walk, so prior information is percolated backwards in time.
Student-t-distributed increments were also explored but the data were not very
informative for the degrees of freedom parameter, and the model predictions
changed very little.

Each poll is considered to be a binomial draw whose probability depends on
the latent national and state (if a poll of an individual race) voter intent,
adjusted for the polling firm&rsquo;s house effects, the type of respondents
(registered voters, likely voters, or all adults), poll-specific error, and
state, regional, and national polling error.

Each of these adjustments is a parameter that the model estimates.  Polling
error cannot be estimated from polling data, and essentially just adds noise to
the model. The distribution of these polling errors is estimated from past
elections’ polling errors.

Election outcomes are simulated by looking at the Monte Carlo draws of the latent 
state and national intent parameters on Election Day. 

Models were fit using [Stan](https://mc-stan.org). 
Model code and data are [available online](https://github.com/CoryMcCartan/president).
[Email me](mailto:cmccartan@g.harvard.edu) with any questions.
</div>

<div class="link-banner">
<span>JUMP TO</span>
<a href="#">Summary</a>
<a href="#how-the-odds-have-changed">Model history</a>
<a href="#race-forecasts">Race forecasts</a>
<a href="#possible-scenarios">Possible scenarios</a>
<a href="#model-components">Model components</a>
</div>


<script src="/election-2020/shared.js"></script>
<script src="charts.js"></script>
<script src="main.js"></script>
<style>
</style>
