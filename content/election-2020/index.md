---
title: 2020 Election Forecasts
description: >
    Statistical models of the 2020 election, built using polling data,
    structural factors, and economic indicators.
date: 2020-03-12
js: [
    "https://d3js.org/d3.v5.min.js",
]
---

<h1>Who will control the government?</h1>

The table below shows all the possible scenarios for the partisan control
of the White House and each house of Congress. Click on the top of each column
to be taken to the corresponding forecast.

<table id="probs">
<col width="30%">
<col width="20%">
<col width="20%">
<col width="30%">

<thead>
<tr>
<th><a href="/projects/president-20/">Presidency &raquo;</a></th>
<th><a href="/projects/senate-20/">Senate &raquo;</a></th>
<th><a href="/projects/us-house-20/">House &raquo;</a></th>
<th>Chances</th>
</tr>
</thead>

<tbody></tbody>
</table>

The probabilities are given as ranges because there isn&rsquo;t enough data to 
accurately model the interdependence of the national presidential, House, and
Senate races; instead, we use modified 
[Fréchet inequalities](https://en.wikipedia.org/wiki/Fr%C3%A9chet_inequalities)
to create ranges.

<style>
    #probs {
        width: 100%;
        margin: 0 auto;
        border-spacing: 6px;
        border-top: 1px solid #444;
        border-bottom: 1px solid #444;
        font-weight: normal;
    }

    #probs th {
        user-select: none;
        padding: 6px;
        line-height: 1.3;
    }
    #probs td {
        line-height: 1.3;
        padding: 12px;
        border-radius: 2px;
    }

    @media screen and (max-width: 540px) {
        #probs {
            font-size: 0.92em;
            border-spacing: 4px;
        }
        #probs th {
            padding: 4px 0;
        }
        #probs td {
            padding: 8px 6px;
        }
    }
</style>

<br />

<div class="promo">
<img src="/election-2020/wh.jpg">
<a href="/projects/president-20/">Presidential Forecast &raquo;</a>
</div>

<div class="promo">
<img src="/election-2020/senate.jpg">
<a href="/projects/senate-20/">Senate Forecast &raquo;</a>
</div>

<div class="promo">
<img src="/election-2020/capitol.jpg">
<a href="/projects/us-house-20/">House Forecast &raquo;</a>
</div>

<style>
.promo {
    width: 100%;
    display: flex;
    background: white;
    font-size: 16pt;
    margin-bottom: 0.5em;
    border-radius: 8px;
    border-bottom: 2px solid #aaa;
}
.promo img {
    width: 50%;
    max-width: 2in;
    border-radius: 8px 0 0 7px;
    align-self: flex-start;
}
.promo a {
    padding: 1em;
    margin: auto;
    text-decoration: none;
}
.promo a:hover {
    color: black;
    text-decoration: underline;
}
.promo a.broken:hover {
    cursor: default;
    text-decoration: none;
}

@media screen and (max-width: 540px) {
    .promo {
        flex-direction: column;
    }

    .promo img {
        max-width: unset;
        width: 100%;
        border-radius: 8px 8px 0 0;
    }
}
</style>

<script src="main.js"></script>
