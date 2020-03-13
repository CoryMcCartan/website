---
title: 2020 Election Forecasts
description: >
    Statistical models of the 2020 election, built using polling data,
    structural factors, and economic indicators.
date: 2020-03-12
---

<div class="promo">
<img src="/election-2020/capitol.jpg">
<a href="/projects/us-house-20/">House Forecast &raquo;</a>
</div>

<div class="promo">
<img src="/election-2020/wh.jpg">
<a class="broken" href="#">Presidential Forecast (Coming Soon)</a>
</div>

<div class="promo">
<img src="/election-2020/senate.jpg">
<a class="broken" href="#">Senate Forecast (Someday)</a>
</div>

<style>
.promo {
    width: 100%;
    display: flex;
    background: white;
    font-size: 20pt;
    margin-bottom: 1em;
    border-radius: 8px;
    border-bottom: 2px solid #aaa;
}
.promo img {
    width: 50%;
    max-width: 3in;
    border-radius: 8px 0 0 7px;
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
