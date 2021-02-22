---
title: "Conditional Forecasts"
description: >
    Explore scenarios and track each candidate's chances of claiming the
    presidency, depending on which states they win—and by how much.
date: 2020-11-03
publishdate: 2020-10-25
slug: election-night
summary: >
    Use this tool to game out various scenarios, or to  make real-time
    election-night forecasts for the presidential race as the results roll in.
images:
    - ./images/enight-promo.png
---

<b><a href="/projects/president-20/" target="_blank">Main presidential forecast &raquo;</a></b>

<b id="loading">This page may take a few seconds to load...</b>

<iframe id="elec-embed" src="https://corymccartan.shinyapps.io/election2020/"></iframe>

<script>
document.querySelector("#elec-embed").onload = function() {
    document.querySelector("#loading").style.display = "none";
};
</script>

<style>
#elec-embed {
    width: 100vw;
    position: absolute;
    left: 0;
    height: 54in;
    border: none;
}
</style>
