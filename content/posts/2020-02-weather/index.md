---
title: On a Streak?
description: >
    Why your city’s weather changes, or doesn’t.
date: 2020-02-18
slug: weather
summary: >
    Streaks are an important part of how we experience a place's weather: it
    matters not just how hot it gets, or how much it rains, but also how long
    these kinds of weather stick around. Mathematically, one way to understand
    these patterns is through Markov chains. Thinking of weather in this way
    can reveal some interesting patterns, and confirm some stereotypes.
images:
    - ./images/2020-02-weather-promo.png
js: [
    "https://cdn.jsdelivr.net/npm/vega@5.9.1", 
    "https://cdn.jsdelivr.net/npm/vega-lite@4.3.1",
    "https://cdn.jsdelivr.net/npm/vega-embed@6.2.2",
    ]
---

<span class="leadin">On September 5, 1997,</span> Los Angeles 
[set a city record](https://www.nytimes.com/1997/09/05/us/los-angeles-sets-record-for-rainless-days.html)
for the most consecutive days without any rain: 198. Just last month, Seattle
set a city record for having had rain
[every single day in January](https://www.washingtonpost.com/weather/2020/01/31/after-29-straight-days-rain-an-intense-atmospheric-river-will-drench-seattle-through-weekend/),
except New Year&rsquo;s Day.

These streaks highlight an important part of how we experience a place's weather:
it matters not just how hot it gets, or how much it rains, but also how long 
these kinds of weather stick around.  Thus Mark Twain's famous quote: "If you
don't like the weather in New England now, just wait a few minutes."

Mathematically, one way to understand these patterns is through 
*[Markov chains](https://en.wikipedia.org/wiki/Markov_chain)*, which are a fancy
way of talking about the picture below. Suppose we live in Pleasantville, USA, 
and it's sunny today. Tomorrow, there's a 70% chance it will still be sunny, and 
a 30% chance it will rain.  If it does rain tomorrow, then there's a 40% chance
it will rain again the day after that, and a 60% chance it will go back to being
sunny. You can imagine your finger tracing out the weather pattern along the
arrows.

{{< figure src="markov.svg" class="w6in" >}}

Thinking of weather as a Markov chain gives us a lot of tools to understand its
behavior.  For example, we can calculate how often it will be sunny or rainy,
and we can estimate how likely we are to have 198 days of sun in a row.
Now---news flash!---the weather changes throughout the year, so we have to
think about the probabilities in the diagram above as changing from day to day.
Sunny streaks are more likely during the summer.

But if we allow for these changes, and we look at not just sun and rain but also
clouds and snow, we can start to get an interesting picture of the weather in a
place.  The next section shows what happens when we use a statistical model to
do this for the largest fifteen or so cities in the U.S.  Try picking different
cities in the drop-down menu and explore how their weather patterns differ.

[[Jump to the second half](#comparing-cities)] &nbsp;&nbsp;
[[Jump to the methodology section](#methodology)]

<figure class="interactive" style="padding: 0 0 1em 0; margin: 3em 0;">

<div style="position: sticky; top: 3.5rem; padding: 1em 0; 
    background: #f4f4f4; z-index: 1; border-bottom: 1px solid #aaaaaa;
    margin-bottom: 0.5em; font-weight: normal">
Find your city:&nbsp;&nbsp;
<select id="city" style="font-family: Overpass; font-size: 11pt; font-weight: bold;">
<option value="atlanta">Atlanta</option>
<option value="boston">Boston</option>
<option value="chicago">Chicago</option>
<option value="dallas">Dallas</option>
<option value="des_moines">Des Moines</option>
<option value="detroit">Detroit</option>
<option value="houston">Houston</option>
<option value="los_angeles">Los Angeles</option>
<option value="miami">Miami</option>
<option value="minneapolis">Minneapolis</option>
<option value="new_york">New York</option>
<option value="philadelphia">Philadelphia</option>
<option value="phoenix">Phoenix</option>
<option value="san_francisco">San Francisco</option>
<option selected value="seattle">Seattle</option>
<option value="washington">Washington, D.C.</option>
</select>
</div>

<p>
How often is it sunny in February? Snowy in September? The chart below shows 
how the mix of weather in <span id="city-name">Seattle</span> varies
throughout the year. Hover over it to see a more detailed breakdown.
</p>

<div id="chart_sst" class="vega-chart" style="margin-bottom: 0.5em"></div>

<p>
Once we've estimated the Markov chain of <span id="city-name">Seattle
</span>&rsquo;s weather, we can use it to figure out how long streaks of
certain kinds of weather should last. And we can average these out across the
four kinds of weather to arrive at a single number which summarizes how 
&ldquo;persistent&rdquo; <span id="city-name">Seattle</span>&rsquo;s weather is: 
does it change every day, or does it stick around for weeks at a time?
</p>

<div style="display: flex; flex-wrap: wrap; margin: 0 -0.5em 1em 0;">
<div id="chart_over_persist" class="vega-chart" style="max-width: 6in; 
    flex: 1 0 48%; min-width: 3in; margin-right: 0.5em;"></div>
<div id="chart_persist" class="vega-chart" style="max-width: 6in; 
    flex: 1 0 48%; min-width: 3in; margin-right: 0.5em;"></div>
</div>

<p>
Finally, we can fully describe a Markov chain by its <i>transition matrix</i>,
which lists the chances of going from one kind of weather to another&mdash;the
numbers along each of the arrows in the diagram above. The chart below
visualizes the transition matrix for <span id="city-name">Seattle</span>; hover
over a rectangle to see the chances of going from one kind of weather today to
another kind tomorrow.  Use the date slider at the bottom to see how these
numbers change throughout the year.
</p>

<div id="chart_matrix" class="vega-chart" style="margin-bottom: 2.5em; max-width: 7in;"></div>

</figure>

# Comparing Cities

One way in which cities differ is in how much their weather changes throughout
the year---how "squiggly" the weather mix diagram from above is, to be precise.
The figure below tries to measure this. Most East Coast cities have a broadly
similar mix of sun and rain throughout the year. In contrast, cities like Miami,
San Francisco, and Seattle have more clearly defined sunny and rainy seasons.
(This is somewhat related to this [excellent
article](https://fivethirtyeight.com/features/which-city-has-the-most-unpredictable-weather/)
about the predictability of weather across the U.S.)

{{< figure src="mix_variance.png" class="w7in" >}}

Other patterns are rather predictable. Ranking cities by the average length
of their sunny streaks yields, predictably, cities in the South and West.
Slightly less predictable is that Seattle's sunny streaks are about as long as
those of most cities in the Northeast and Midwest.

{{< figure src="sun_streak.png" class="w7in" >}}

The patterns for rain are even less surprising: except for Seattle, San
Francisco, and Miami, it rains for around 1.7 days at a time in most cities.
Phoenix has the shortest average rainy streak, at just over 1.5 days.

{{< figure src="rain_streak.png" class="w7in" >}}

And on the subject of rain, it's informative to look at how the *amount* of rain
a city gets corresponds to the *number* of rainy days it gets. While for most
cities these go hand in hand, in Seattle, rainfall is spread out over a much
larger number of days.  While the city receives less rain than D.C., New York,
and Houston, it has more rainy days---over 140, on average---than any other major
city in the U.S. Does this fairly qualify it for the title of "Rainiest City"?
You decide.

{{< figure src="city_rain.png" class="w6in" >}}


# Methodology

### Fitting the Markov chains
Given the weather on a day, the Markovianness of the process
means that the weather on the next day is drawn from a categorical distribution,
with probabilities given by the corresponding column in the transition matrix.
The Markov chains used here are time-inhomogeneous: the transition matrix changes
from day to day.  The transition matrix probabilities were assumed to vary in
time along Gaussian radial-basis splines (taking into account the modular
nature of dates around year boundaries), with six knots spaced evenly
throughout the year.

The transition probabilities at each knot were given a Dirichlet(1) prior; this,
combined with the categorical likelihood, allowed for a slight computational
shortcut. Each year was broken up into 53 weeks (with the last week shorter
than 7 days), and the number of transitions from each kind of weather to the
other, across all the years of data, was counted. Then these counts were
modelled from a multinomial distribution, with transition probabilities coming
from the above splines.

Once the model was fit to each city's data (using
[Stan](https://mc-stan.org/)), a transition matrix could be drawn for every
week (or day, if desired) of the year, and this transition matrix could be
solved for its steady-state distribution using its eigendecomposition.  This
yielded the weather mixture charts. 

The diagonal of the estimated transition matrices represent the probability of 
staying in the same weather state from one day to the next. Averaging these
probabilities across the four weather types (a weighted average, with weights
proportional to the steady-state probabilities) yielded a composite probability
of maintaining the current weather.  Markovianness then implies that the number
of days at a certain state follows a geometric distribution; the average streak
length is then easily calculated as the reciprocal of the probability of a 
change in the weather.

### Data 

Weather data came from [NOAA's database](ftp://ftp.ncdc.noaa.gov/pub/data/ghcn/daily/).
A day was classified as cloudy if the sun shone for less than 30% of the day.
Most cities' weather stations had around 35 years where precipitation, snowfall,
and cloud cover were measured every day.


<script src="charts.js"></script>
<style>
    #vg-tooltip-element * {
        font-family: Overpass;
        font-size: 10pt;
        line-height: 1.1;
    }
    #vg-tooltip-element td.key {
        text-transform: uppercase;
        font-size: 0.9em;
    }
    #vg-tooltip-element tr:first-child td.value {
        font-weight: bold;
    }

    .vega-bind {
        display: flex;
    }
    .vega-bind-name {
        margin-right: 0.5em;
        font-weight: normal;
    }
    .vega-bind label {
        display: block;
        width: 7em;
        font-size: 1.2em;
        text-align: right;
        font-weight: bold;
    }
    .vega-bind input[type=range] {
        flex-grow: 1;
        -webkit-appearance: none;  /* Override default CSS styles */
        appearance: none;
        outline: none;
        height: 4px;
        margin: auto;
        border-radius: 2px;
        background: #aaaaaa;
    }
    .vega-bind input[type=range]::-webkit-slider-thumb {
        -webkit-appearance: none; /* Override default look */
        appearance: none;
        width: 20px; 
        height: 20px; 
        border-radius: 20px;
        border: 2px solid #f4f4f4;
        background: #808fbb; 
        cursor: pointer; 
    }
    .vega-bind input[type=range]::-moz-range-thumb {
        width: 16px; 
        height: 16px; 
        border-radius: 8px;
        background: #808fbb; 
        cursor: pointer; 
    }
</style>
