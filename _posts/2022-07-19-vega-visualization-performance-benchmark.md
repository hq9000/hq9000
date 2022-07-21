---
title: Vega Visualization Performance benchmark
--- 

## Table of contents

- [Abstract (TLDR)](#abstract-tldr)
- [What is Vega](#what-is-vega)
- [Interactive client-side graphs on web pages with
    Vega](#interactive-client-side-graphs-on-web-pages-with-vega)
- [Problems scaling Vega](#problems-scaling-vega)
- [Benchmark](#benchmark)
    -   [Variables](#variables)
- [Observations](#observations)
    -   [1000 datapoints](#datapoints)
    -   [5000 datapoints](#datapoints-1)
    -   [10000 datapoints](#datapoints-2)
    -   [30k datapoints](#k-datapoints)
- [Performance profile](#performance-profile)
- [Conclusions](#conclusions)


## Abstract (TLDR)

Vega is a visualization grammar (a language) and a library for server- and client-side visualizations. A live benchmark showing client-side performance of Vega on differently sized datasets is presented. A Python program that generate experiments used in the article is presented as well. Vega is shown to scale well to up to 10000 datapoints. 

The spec/data generator - a Python program used to set up the experiments, is [here](https://github.com/hq9000/vis-study).

![image](https://user-images.githubusercontent.com/21345604/179940839-b9866534-9016-4f0c-a607-d9fc02badbd2.png)

## What is Vega

Vega is a "visualization grammar", essentially, a specification language and a JavaScript library to interpret this grammar (both in browser and server-side). Vega allows creating interactive graphs, called "visualizations", in a declarative way. Declarative here means requiring no coding in traditional sense, we only write a JSON specification. For example, the picture above is a result of rendering [this specification](https://grechin.org/articles/vega_performance/generated/specs/01_points-1000_format-json_categories-14_attributes-2_renderer-canvas_spec.json). 

Vega is widely used in scientific and business circles and has a thriving community, [great documentation](https://vega.github.io/vega/docs/) and [tutorials](https://vega.github.io/vega/tutorials/).

The "grammar" is far from trivial, but once you get a hang of it, creating graphs can be relatively painless and even enjoyable process. The docs are extremely helpful and definitely worth checking out. 
There is also a simplified version of the framework called ["Vega Lite"](https://vega.github.io/vega-lite/)


## Interactive client-side graphs on web pages with Vega

One of the most prominent use cases of Vega is the following:

* the data to be visualized is stored somewhere as `json` or `csv`
* a declarative `json` specification is embedded into the page, or loaded from the outside
* a JavaScript runtime of Vega is loaded as well (they provide it via CDN)
* and viola, a juicy interactive graph is there on the page

see the above in action [here](https://grechin.org/articles/vega_performance/generated/01_points-1000_format-json_categories-14_attributes-2_renderer-canvas.html).

Note that in the use case above, all the heavy lifting of visualizing things is done by the client (a machine running your browser). Once your data and visualization specification are loaded to the browser, it is your PC and your PC only that is responsible for the visualization, no server involved.

## Problems scaling Vega

For reasonably sized datasets (the definition of "reasonably" is, in fact, the main question of this article) client-side Vega works flawlessly. However, as data starts getting big, the performance bottlenecks are becoming evident. This is not to say that Vega is not performant, but rather that any frontend-based visualization is bound to have scalability issues outside its comfort zone (in terms of dataset size).

## Benchmark

Keeping the above in mind, I got curious about how far we can actually push it until gets unusable. Knowing some ballpark figures might help me and others to quickly get some rough idea whether client-side Vega will work in particular use cases. 

To answer this question, a simple spec of a scatter plot showing multi-attribute datapoints was created using a [programmatic generator](https://github.com/hq9000/vis-study).

The properties of the data are:
- x, y - the center of the circle
- category - the fictional category the point belongs to, this affects the color
- attr_0 - attr_4 - a real-valued attributes without any specific meaning except `attr_0` that defines the size of the circle

The expected interactive behaviors:
- when hovering over a circle, all attributes are shown as a concatenated string
- clicking on a category in legend area highlights datapoints belonging to this category

### Variables

the graph described above was built for different values of:
- dataset size (1000, 5000, 10 000, 30 000 points)
- format of input data (`csv` or `json`)
- the renderer (`canvas` or `svg`)

giving us in total 4 * 2 * 2 = 16 different experiments. You can find and check all of them [here](https://grechin.org/articles/vega_performance/generated/index.html).

## Observations

Here I describe my experiences and conclusions after testing the graphs in my setup: Linux, Chrome, a decent i5-based laptop 

### 1000 datapoints

I have no problems at all interacting with the visualization when dataset size is at 1000. 

Neither do I perceive any difference when using `canvas` or `svg` as a renderer.

* [vega with 1k datapoints and svg renderer](https://grechin.org/articles/vega_performance/generated/09_points-1000_format-json_categories-14_attributes-2_renderer-svg.html)
* [vega with 1k datapoints and canvas renderer](https://grechin.org/articles/vega_performance/generated/01_points-1000_format-json_categories-14_attributes-2_renderer-canvas.html)

### 5000 datapoints

At 5000 datapoints, it gets very slightly more sluggish, although I would probably not notice it if I didn't pay attention:

* [vega with 5k datapoints and canvas renderer](https://grechin.org/articles/vega_performance/generated/02_points-5000_format-json_categories-14_attributes-2_renderer-canvas.html)
* [vega with 5k datapoints and svg renderer](https://grechin.org/articles/vega_performance/generated/10_points-5000_format-json_categories-14_attributes-2_renderer-svg.html)

Surprisingly, `canvas` performance is still on par with `svg` one.

### 10000 datapoints

At 10k it gets a little hot. Although the rendering itself takes quite reasonable time, the "show attributes on hover" behaviour is now definitely sluggish (when using `canvas` as renderer).

* [vega with 10k datapoints and canvas renderer](https://grechin.org/articles/vega_performance/generated/03_points-10000_format-json_categories-14_attributes-2_renderer-canvas.html)
* [vega with 10k datapoints and svg renderer](https://grechin.org/articles/vega_performance/generated/11_points-10000_format-json_categories-14_attributes-2_renderer-svg.html)

`svg` renderer feels, again, similar to canvas in terms of rendering, and, surprisingly, shows noticeably better "hover" performance. This is something I did not expect at all. I theorise that somehow `svg` renderer uses browser compiled routines to see which circle we are "hovering" over, as opposed to `canvas` where Vega has to rely on JavaScript interpreter to infer that.

### 30k datapoints
* <a href="https://grechin.org/articles/vega_performance/generated/04_points-30000_format-json_categories-14_attributes-2_renderer-canvas.html" target="_blank">vega with 30k datapoints and canvas renderer</a>
* [vega with 30k datapoints and svg renderer](https://grechin.org/articles/vega_performance/generated/12_points-30000_format-json_categories-14_attributes-2_renderer-svg.html)
    
well, they both still work, I would say. They show me the picture without waiting time being unbearable (though it does give a sluggish impression). With `svg` renderer, I see "hover" working unreliably (not showing anything sometimes). Hovering in `canvas`-based graph is more reliable but the delay is very high, up to the point of making it unusable.  

All in all, I think that 30k is already too much for Vega to handle.

## Performance profile

Here I put some screenshots of Chrome profiler to get some quantitative data.

![image](https://user-images.githubusercontent.com/21345604/180155274-da3820c7-2b8b-4394-8a65-9ab681806c70.png)

![image](https://user-images.githubusercontent.com/21345604/180155525-96664d7a-3058-4366-bbbc-511c1d9aedd0.png)

## Conclusions

So we have these three competing demands:
* responsiveness
* size of data being displayed (the bigger the better)
* speed of rendering

and we would want all three to be satisfied at the same time.

I would say, based on the experiments I performed, the sweet spot is somewhere around 7500 datapoints. Anything above, although somewhat workable, at least up to 30k, is already not too comfortable to interact with.

The most surprising discovery for me was that `svg` renderer does not show any immediately obvious inferiority in comparison with `canvas`, and in some respects and on certain data sizes gives, in fact, better performance (I'm referring to hover behaviour at 10000k). 

Another noteworthy finding is that there is no noticeable performance difference when using `csv` or `json` as data format.

So 10000 seem to be ok, but another point is whether we really want to display this much data. Several thousand facts on the same picture is already too much for any human being to digest. So further scaling should be possible by dynamically loading small portions of data and performing server-side aggregation so that at any given point, the graphical frontend has a comfortably sized data to display.

