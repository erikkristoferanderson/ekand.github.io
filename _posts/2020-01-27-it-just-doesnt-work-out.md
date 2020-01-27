---
layout: post
title: When things don't work out
---
"Sometimes I try to do things, and it just doesn't work out the way I want it to." - Mike Muir

On my second project at Metis, things didn't turn out the way I wanted them to. But it wasn't a complete bust.

I took on the perhaps ambitious task of predicting a musical album's success on the Rolling Stone top albums chart using linear regression. There turned out to be a few issues with this, as I'll describe below. However, through exploratory data analysis, I was able to learn some useful things, and I'll start there.

In all of the characteristics I investigated, the albums on this chart were largely similar. For example, nearly all of the albums had a length between 12 and 18 tracks and had loudness around -7 on a scale from negative infinity to 0, 0 being the loudest possible under the digital encoding scheme.

This is useful information to anyone trying to land a spot on this chart, but it doesn't where an album will fall on the chart. Here we come to the failure of the linear model. I simply found no linear correlation between the things features I tracked and the chart position of a given album.

It's instructive to speculate why this may be. One possible reason is the all of the albums on this chart are similar because of selection bias: only successful records even make it on to the chart, and successful records may tend to be quite similar.

Also, there may be ineffable qualities to music that can't be captured in the sort of metrics I was considering.

-----

