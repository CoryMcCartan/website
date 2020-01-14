---
title: "Swirling Fractals"
description: "An animated Julia-set journey"
date: 2015-04-01
summary: >
    Corresponding to each point in and around the Mandelbrot set is a Julia
    set. If we start with a point near the origin, and move it in a circle
    around the main bulb of the Mandelbrot set, the series of corresponding
    Julia sets morph beautifully into one another.
---

The [Mandelbrot set](https://en.wikipedia.org/wiki/Mandelbrot_set), generated
by iterating the map _f(z)=z<sup>2</sup>+c_, looks something like this, when
colored by the number of iterations to blowup:

{{< figure src="https://upload.wikimedia.org/wikipedia/commons/2/21/Mandel_zoom_00_mandelbrot_set.jpg"
class="w100" >}}

Corresponding to each point in and around the Mandelbrot set is a Julia set, 
created by a similar iteration. In fact, a point is in the Mandelbrot set if
and only if its Julia set is connected. If we start with a point near the origin,
and move it in a circle around the main bulb of the Mandelbrot set, the series
of corresponding Julia sets morph beautifully into one another, slowly
completing a counter-clockwise rotation.

<iframe src="https://corymccartan.github.io/animated-julia-sets/" 
style="width: 100%; border: none" height=640>WebGL required!</iframe>

