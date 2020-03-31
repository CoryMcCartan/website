---
title: "Not Just Like the Flu"
description: "Right now, chances are that someone you know will die of COVID-19."
date: 2020-03-22
slug: covid-deaths
summary: >
    All of the numbers floating around about the coronavirus can obscure the one 
    simple fact that we must all remember if we are to be disciplined enough in
    our social distancing: this pandemic is deadly serious, and if we don&rsquo;t
    continue to take drastic action, at an individual and societal level, then
    someone you know will probably die.
images:
    - ./2020/03/covid-deaths/covid_cover.jpg
js: ["https://d3js.org/d3.v5.min.js"]
---

{{< figure src="covid_cover.jpg" class="w100" alt="Hospital in Iran" >}}

<span class="leadin">There have been a lot of numbers</span> thrown around 
recently about the scope and severity of the coronavirus pandemic.  As of Sunday,
there are 32,000 confirmed cases in the United States.  New York governor Andrew
Cuomo is saying that 40&ndash;80% of the state could contract the disease. 
Others estimate that 30% of the U.S. population will become infected. Estimates
of the fatality rate of the disease vary wildly.  

There&rsquo;s a lot we just don&rsquo;t know, and there&rsquo;s a lot that
depends on how successful we are at flattening the curve through social
distancing, improved testing, and other interventions.  

But all of these numbers, and the uncertainty surrounding them, can obscure the
one simple fact that we must all remember if we are to be disciplined enough in
our social distancing: this pandemic is deadly serious, and if we don&rsquo;t
continue to take drastic action, at an individual and societal level, then
someone you know will probably die.

The graph below shows some of our best estimates of the fatality rate of COVID-19
among people who contract the disease and show any symptoms, from a 
[very recent paper](https://www.nature.com/articles/s41591-020-0822-7) in 
*Nature* by Wu et al.

{{< figure src="scfr.png" class="w6in" >}}

The researchers estimate that overall, 1.4% of symptomatic patients will die,
and they assume that around half of all people who are infected show no symptoms.
Combining that with estimates that 30&ndash;80% of the 7.7 billion people on 
Earth will be infected, and we're looking at between 21 and 43 *million*
deaths worldwide.

What does this mean for you, personally? Fill out the boxes below.

<section class="interactive">
<div class="sliders">
<div class="slider-box">
<b style="font-size: 1.3rem;">Infection rate</b>&nbsp;&nbsp;
<input id="inf_rate" type="range" min=1 max=100 value=50 step=1 />
<label id="l_ir" for="inf_rate"></label>
</div>
How many will be infected with the virus. Current estimates are 30&ndash;80%.
The numbers below assume that around half of those infected will not show symptoms.

<div class="slider-box">
<b style="font-size: 1.3rem;">Fatality rate</b>&nbsp;&nbsp;
<input id="scfr" type="range" min=0.1 max=3 value=1.4 step=0.1 />
<label id="l_scfr" for="scfr"></label>
</div>
What fraction of those who show symptoms will die. 
Current estimates are 0.9&ndash;2.1%.
</div>

<h3>How many people do you know in each age group?</h3>
<div id="cols">
<div id="lcol">
<table id="age-groups">
<tr>
<td>0&ndash;9</td>
<td><input id="num_0009" type="number" min=0 value=5 /></td>
</tr>
<tr>
<td>10&ndash;19</td>
<td><input id="num_1019" type="number" min=0 value=15 /></td>
</tr>
<tr>
<td>20&ndash;29</td>
<td><input id="num_2029" type="number" min=0 value=280 /></td>
</tr>
<tr>
<td>30&ndash;39</td>
<td><input id="num_3039" type="number" min=0 value=100 /></td>
</tr>
<tr>
<td>40&ndash;49</td>
<td><input id="num_4049" type="number" min=0 value=40 /></td>
</tr>
<tr>
<td>50&ndash;59</td>
<td><input id="num_5059" type="number" min=0 value=40 /></td>
</tr>
<tr>
<td>60&ndash;69</td>
<td><input id="num_6069" type="number" min=0 value=60 /></td>
</tr>
<tr>
<td>70&ndash;79</td>
<td><input id="num_7079" type="number" min=0 value=40 /></td>
</tr>
<tr>
<td>80+</td>
<td><input id="num_8000" type="number" min=0 value=20 /></td>
</tr>
<tr>
<td style="text-decoration: underline">Total</td>
<td style="font-weight: bold; font-size: 1.1rem;" id="total"></td>
</tr>
</table>
(Most Americans know between 300 and 800 people.)
</div>

<div id="rcol">

<div class="estimate" id="est_deaths">
On average, <b></b> people you know are expected to die.
</div>

<div class="estimate" id="prob_one">
There is a <b></b> chance that at least one person you know dies.
</div>

</div>
</div>

</section>

To reiterate, there is still *a lot* of uncertainty about the fatality rates
and even more about how many people will eventually become infected. But if
we want to minimize the scale of this global tragedy, each of us must take
the disease seriously and do everything we can to follow public health
guidelines.

<p style="text-align: center;">
<b><a href="https://www.coronavirus.gov/" target="_blank">
    Up-to-date information and guidelines &raquo;
</a></b>
</p>

<script src="covid.js"></script>
<style>
#cols {
    display: flex;
    flex-wrap: wrap;
}

#cols > #lcol {
    margin-right: 1rem;
}
#cols > #rcol {
    flex-grow: 1;
    flex-basis: 360px;
}

.slider-box {
    display: flex;
    align-items: baseline;
    max-width: 480px;
}

.estimate {
    background: #eea0aa;
    padding: 0.75em;
    font-size: 1.5rem;
    margin: 3px 0 0.75em 0;
    border-radius: 2px;
    width: 100%;
}

#age-groups {
    width: 100%;
    max-width: 360px;
}

#age-groups td:first-child {
    font-size: 1.1rem;
    min-width: 5em;
    font-weight: bold;
}

label {
    font-size: 1.7rem;
    color: #666;
    font-weight: bold;
    margin-left: 4px;
    width: 2.8em;
    text-align: right;
}

input[type=number] {
    padding: 0.3em;
    border: 1px solid #808fbb;
    border-radius: 2px;
    outline: none;
    font-size: 1.1rem;
    width: 100%;
}

input[type=range] {
    flex-grow: 1;
    -webkit-appearance: none;  /* Override default CSS styles */
    appearance: none;
    outline: none;
    height: 4px;
    margin: auto;
    position: relative;
    top: 3px;
    border-radius: 2px;
    background: #aaaaaa;
}
input[type=range]::-webkit-slider-thumb {
    -webkit-appearance: none; /* Override default look */
    appearance: none;
    width: 20px; 
    height: 20px; 
    border-radius: 20px;
    border: 2px solid #f4f4f4;
    background: #808fbb; 
    cursor: pointer; 
}
input[type=range]::-moz-range-thumb {
    width: 16px; 
    height: 16px; 
    border-radius: 8px;
    background: #808fbb; 
    cursor: pointer; 
}

@media screen and (max-width: 750px) {
    .sliders {
        position: sticky;
        background: #f4f4f4;
        top: 50px;
        padding-bottom: 0.5em;
        border-bottom: 1px solid #666;
        font-size: 0.95rem;
        line-height: 1.1;
    }
}
</style>
