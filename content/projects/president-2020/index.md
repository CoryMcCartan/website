---
title: 2020 Presidential Forecast
description: >
    Four more years? Or a new direction? What the polls, the economy, and
    history can tell us.
date: 2020-03-30
slug: president-20
featured: true
images:
    - /election-2020/pres_promo.png
js: [
    "https://d3js.org/d3.v5.min.js",
    "https://d3js.org/topojson.v2.min.js"
]
css: [
    "/projects/president-20/graphics.css",
    "/election-2020/shared.css",
]
---

<div id="forecast-links" class="tabs">
<span>
<a href="/election-2020/" class="mainlink">2020 FORECASTS</a>
<img src="/election-2020/flag.gif" 
    style="height: 32px; margin: -8px 0 -11px 6px;">
</span>
<a href="/projects/president-20/" class="current">President</a>
<a href="/projects/senate-20/">Senate</a>
<a href="/projects/us-house-20/">House</a>
</div>


<section id="categories"></section>

<section class="banner">
<span class="text"></span>
<span class="updated"></span>
</section>

<!-- 
<div class="editor-note">
<h2>NOTE</h2>
<p>
This model relies on second-quarter GDP growth to build a prior estimate of
the election day vote share.  On Thursday, July 30, advance Q2 GDP estimates
were released which were substantially below Federal Reserve forecasts, and
much worse than any GDP data since records have been kept.  Directly inputting
this GDP estimate into the model here would not provide an accurate picture of
the economic and political uncertainty resulting from the coronavirus pandemic.
</p>
<p>
For the time being, the model will be using an average of Q2 and Q3 GDP growth
to build the prior, with the former coming from the advance estimate and the 
latter from the Federal Reserve forecasts.
</p>
<div style="color: #877; font-size: 0.85rem; text-align: right;">
2:40 p.m., July 30, 2020
</div>
</div>
-->

# The electoral map

Hover over a state to see the chances each candidate has of winning it, and
click on a state to see more detailed forecasts.

<section id="map"></section>

<div style="display: flex; flex-wrap: wrap; justify-content: center;">
<button id="sim_elec">Simulate an election</button>
<button disabled id="reset_map">Reset map</button>
<div id="map_sim_result" class="sim_result"></div>
</div>

<span id="cand_lean"></span> has a <span id="prob_win"></span> chance of
winning, but what does that really mean? There is a wide range of possible
outcomes, at the state level and nationally.  Click the button above to
randomly simulate a possible election outcome. 

### All the possible outcomes

<section id="histogram"></section>

The histogram above shows the distribution of electoral votes that the model
is currently predicting. The wide range of possible outcomes reflects the 
inherent uncertainty in predicting elections. The fact that small numbers of
votes can flip a state from one candidate to another, along with all of that
state&rsquo;s electoral votes, means that this distribution is very spiky, unlike
a normal bell curve.

# How the odds have changed

The model works by first building a [structural forecast](#prior-model) for the
national race and the race in each state, based on economic indicators, the
president&rsquo;s approval rating, past election results, the home states of each of
the candidates, and incumbency and regional effects. 

The model then uses state and national polls to [estimate public
opinion](#national-polling) in every state and nationally, and makes a forecast
for Election Day by simulating thousands of possible elections, taking into
account the structural forecast based on the non-poll factors. 

Of course, there is a lot of uncertainty in elections and polling. The model
takes this into account, combining uncertainty across all of these factors to
arrive at an overall distribution of the number of electoral votes that each
candidate will win. From this distribution, we can figure out the chances that
Biden and Trump will win at least 270 seats and claim the White House.

The model is updated regularly as new economic and polling data come in. The
charts below show how the forecast has evolved over time.

<div id="history_tabs">
<div class="tabs">
<a href="#prob_history" class="current">Overall odds</a>
<a href="#ev_history">Electoral votes</a>
<a href="#pv_history">Popular vote</a>
</div>

<section id="prob_history">
<div class="chart"></div>

This chart shows how the model&rsquo;s estimate of the overall probability of
winning the presidency has changed over time. Because the model is based on
random simulations, these probabilities will naturally jump around a bit, so a
shift of a few percentage points in either direction doesn&rsquo;t usually
reflect a change in the state of the race.

</section>

<section id="ev_history">
<div class="chart"></div>

This char shows the estimated range of electoral votes that Biden will
win, and how it has changed over time. 

The range will narrow as we approach the election, because we will have more
information, and there will be less time for the race to be upended by an
economic or political development.

The outer band above is an **90% credible interval**, meaning that based on the
information available at the time the forecast was made, there was an 90%
chance that Biden would win a number of electoral votes somewhere in that
interval. The inner band shows a **50% credible interval**.
</section>

<section id="pv_history">
<div class="chart"></div>

This chart shows the estimated popular vote margin (excluding write-ins and
third party candidates), and how it has changed over time. Right now, the model
estimates that Biden has a <span id="prob_pop"></span> chance of winning the
popular vote.

The range will narrow as we approach the election, because we will have more
information, and there will be less time for the race to be upended by an
economic or political development.

The outer band above is an **90% credible interval**, meaning that based on the
information available at the time the forecast was made, there was an 90%
chance that Biden would earn a popular vote total somewhere in that
interval. The inner band shows a **50% credible interval**.

</section>

</div>

# State forecasts

The table below summarizes the race in every state, including the forecasted
vote share (excluding write-ins and third parties), probability of winning, and
some measurements of how important each state is to the overall race. You can
click on the column headers in order to sort the table, or click on a state to
see more details.

What does it mean to say that a state decided an election?  If we think about
listing states in order of their support for the winning candidate, and then
going down the list, counting up the cumulative number of electoral votes,
the deciding state is the first state on the list where the cumulative votes
are above 270. In 2016, the deciding state was Wisconsin; in 2012, it was
Colorado. (These states are also called 
["tipping-point states"](https://en.wikipedia.org/wiki/Tipping-point_state).)

If we divide the chance that a state decides the election by the number of 
voters in that state, we get the chance that a single voter will decide the
election. If we compare this chance to the average chance across the country,
we get a measure of how much relative power voters in every state have to
determine the election.  Small states where the election is close have the most
powerful voters, whereas large states or states where the election isn&rsquo;t very
close have the least powerful voters.

<table id="states" class="minim">
<col width="18%">
<col width="10%">
<col width="22%">
<col width="22%">
<col width="8%">
<col width="11%">
<col width="9%">

<thead>
<tr>
<th data-kind="state" data-asc="1">State</th>
<th data-kind="prob" data-asc="0" class="small">Chances of winning</th>
<th data-kind="vote" data-asc="0" colspan="2">
Estimated vote share
<div style="font-weight: 300; color: #666; font-size: 0.85em; margin-top: 2px; line-height: 1;">
Bands show 50% and 90% credible intervals</div>
</th>
<th data-kind="margin" data-asc="1">Margin</th>
<th data-kind="tipping" data-asc="0" class="small">
Chance&nbsp;of deciding election</th>
<th data-kind="power" data-asc="0" class="small">Relative voter power</th>
</tr>
</thead>

<tbody></tbody>
</table>

<div style="display: flex; justify-content: space-around; margin-bottom: 2em;">
<button id="show">Show more states</button>
</div>


Select a state to see detailed forecasts and how they&rsquo;ve changed over time.

<select id="state">
</select>

<span id="selected_state"></span> has <b><span id="state_ev"></span> electoral
votes</b> and voted for <span id="state_2016"></span> and 
<span id="state_2012"></span>. 
<span hidden id="split_ev">The state awards two electoral votes to the statewide
winner and one electoral vote to the winner of each of its congressional
districts; this detail is not accounted for in the model.</span>
<span id="state_polls"></span>

<section id="state_history"></section>

[See above](#state-forecasts) for more information about what "deciding the
election" and "relative voter importance" mean.

<section id="tipping_history" style="margin-top: -1em"></section>


# Possible scenarios

Usually, whichever candidate wins the popular vote wins the presidency, but as
the 2016 election showed, that&rsquo;s not always the case---the electoral vote winner
could have less than a majority of the popular vote.  And there might not even
be a clear winner of the Electoral College on election night:

<ul>
<li>
There is a <b id="prob_tie"></b> chance of an exact tie in the Electoral College,
in which case the election would be thrown to Congress.
</li>
<li>
There is a <b id="prob_recount"></b> chance that the deciding state will have a
vote margin less than half a percentage point that will trigger a recount, which
could take weeks. Think Florida in 2000.
</li>
</ul>

As for the other scenarios, it&rsquo;s much more likely that Biden will win the 
popular vote but lose the election, like Clinton in 2016, than that the same
will happen to Trump.

<section id="pop_ev_history"></section>

### What happens if&hellip; ?

There are many paths to 270 electoral votes. No one state is critical for a 
candidate to win. But states&rsquo; outcomes are highly correlated with one another,
and winning one state can be a sign of strength elsewhere. 

The buttons below are for the fifteen states most likely to decide the
election.  Click them to cycle through hypothetical winners and play out
different scenarios. What if Trump wins Florida but Biden wins Pennsylvania?
What if Biden sweeps the Rust Belt? You could even use these buttons on
election night to provide live estimates of the race as each state is called.

<div id="state_buttons"></div>
<a id="reset_states">Reset all</a>

<div id="filter_warning" class="sim_result"></div>
<div id="filter_sum" class="sim_result"></div>
<div id="filter_prob"></div>
<div id="scenario_prob" style="color: #666; margin-top: 0.25em;"></div>


# Model components

The model works by combining various structural, non-polling factors with state
and national polls to arrive at an overall forecast for the election. The
sections below provide more detail on each of these components.

### Prior model

The first component of the model is a so-called "prior" guess about what the
national popular vote will be.  This is based on a [simple but accurate 
model](https://www.nytimes.com/2016/05/11/upshot/voters-fears-about-trump-may-outweigh-wish-for-change.html)
by political scientist Alan Abramowitz, which has correctly called the winner
of the popular vote in every post-World War II election except 2016, where it
predicted Trump would win the popular vote. The model takes three inputs:
<ul>
<li>The average of second- and third-quarter annualized GDP growth is estimated
by the New York branch of the Federal Reserve at <b id="q2_gdp"></b>.</li>

<li>The president&rsquo;s current approval rating (among those stating an
opinion) is <b id="pres_appr"></b>.</li>

<li>Trump is a first-term incumbent.</li>
</ul>

These give us a prior expectation of the national popular (excluding write-ins
and third parties) vote of <b id="natl_prior"></b> for Biden.

The second part of the model is a prior guess about how the vote in each
state will differ from the national vote.  The best predictor of this 
differential is the results in the last two elections, but the model also
adjusts for year and region variation, incumbency effects, and home state
effects---the tendency of presidential (and to some extent vice-presidential)
candidates to over-perform in their home states.

### National polling

With the initial prior guesses in hand, the model then combines them with 
polling data to arrive at an election-day forecast.

Support for Biden or Trump in polls now is obviously not necessarily the same
as their vote share on Election Day. The model adjusts and averages polls to
estimate public opinion for each 3-day period of the race up to the present
day, and then forecasts how it will change toward November. 

Since Super Tuesday, <b id="n_polls"></b> polls have been conducted. Polls
conducted early on in the race (especially national polls) don&rsquo;t have much
impact on the overall forecast, since voters&rsquo; opinions will change a lot
before November. But as we get closer to Election Day, the polls become more
informative about the final result.

The chart below shows the model&rsquo;s estimates of voters&rsquo; margin of support for 
the candidates for each point in the race. The rightmost values on this chart
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

The above [components section](#model-components) lays out the general overview
of the model. All submodels operate on the logit scale.  The prior models for the
national vote and state differentials are linear models (with random effects
for the state model); Cauchy(0, 2.5) priors on scaled and centered predictors
were used. The random effects in the state prior model give the predicted state
outcomes a pairwise correlation of around 0.5; this correlation is rather
sensitive to the model specification but does have an impact on final inferences.
More robust estimation of the state result covariances is an area in which the
model could be improved.

The polling model is similar to a 2016 election model by 
[Pierre-Antoine Kremp](https://www.slate.com/features/pkremp_forecast/report.html),
which in turn is built on Drew Linzer&rsquo;s [dynamic Bayesian forecasting 
model](https://votamatic.org/wp-content/uploads/2013/07/Linzer-JASA13.pdf).
In contrast to those models, this one incorporates a critical adjustment for
the bias of registered-voter and all-adult polls, uses past election data
to estimate polling errors, and uses more informative priors on national 
and state outcomes, built from the linear models described above.

Essentially, there is a latent national voter intent, and latent state
differentials (how much more or less Democratic the state is than the national
vote), which evolve as a random walk with Gaussian increments in 3-day and
3-week steps (the states&rsquo; walk has larger steps for computational reasons).
The national and state priors become priors on the final step of the random
walk, so prior information is percolated backwards in time.
Student-t-distributed increments were also explored but the data were not very
informative for the degrees of freedom parameter, and the model predictions
changed very little.

Each poll is considered to be a binomial draw whose probability depends on
the latent national and state (if a state poll) voter intent, adjusted for the
polling firm&rsquo;s house effects, the type of respondents (registered voters,
likely voters, or all adults), poll-specific error, and state, regional, and
national polling error.

Each of these adjustments is a parameter that the model estimates.  Polling
error cannot be estimated from polling data, and essentially just adds noise to
the model. The distribution of these polling errors is estimated from past
elections’ polling errors. For computational reasons, states&rsquo; polling errors
after accounting for national and regional error are assumed to be i.i.d.
This yields pairwise correlations of state polling errors of around 0.7. In
reality, polling errors (and final outcomes; see above) are likely to be
more correlated in geographically close and demographically similar states; this
remains an area of potential improvement.

Election outcomes are simulated by looking at the Monte Carlo draws of the latent 
state and national intent parameters on Election Day. The congressional-district 
based electoral vote allocation rules in Nebraska and Maine are not modelled;
elections in which one of the states&rsquo; votes go to a candidate other than the 
statewide winner are unlikely to be elections in which the outcome is decided 
by a single electoral vote.

Fit to data from the 1972 to 2012 elections and run on 2016 polling and
economic data, the model identified the Rust Belt as an area of weakness for
Clinton and consistently gave her a less-than-50% chance of winning the election,
in contrast to all other major polling aggregators in 2016.  Of course,
hindsight is 20/20, and some knowledge about the final result inevitably crept
into model development and testing. But in contrast to most aggregators,
the model is fully Bayesian and therefore optimally blends structural forecasts
like Abramowitz&rsquo;s time-for-change model with polling data, rather than making
[ad-hoc weighting adjustments](https://fivethirtyeight.com/features/a-users-guide-to-fivethirtyeights-2016-general-election-forecast/#attachment_118876)
or [ignoring the latter entirely](https://www.nytimes.com/interactive/2016/upshot/presidential-polls-forecast.html).

Models were fit using [Stan](https://mc-stan.org). 
Model code and data are [available online](https://github.com/CoryMcCartan/president).
[Email me](mailto:cmccartan@g.harvard.edu) with any questions.
</div>

<div class="link-banner">
<span>JUMP TO</span>
<a href="#">Summary</a>
<a href="#how-the-odds-have-changed">Model history</a>
<a href="#state-forecasts">State forecasts</a>
<a href="#possible-scenarios">Possible scenarios</a>
<a href="#model-components">Model components</a>
</div>


<script src="/election-2020/shared.js"></script>
<script src="charts.js"></script>
<script src="main.js"></script>
<style>
</style>
