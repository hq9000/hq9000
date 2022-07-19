## Abstract

A benchmark showing client-side performance of Vega on differently sized datasets is provided. Real interactive graphs are there in the articles for readers to play with.

## What is Vega

Vega is a visualization grammar allowing to create interactive graphs, or visualizations, in a declarative way, by creating a json definition. It is widely used in scientific and business circles and has a thriving community and great documentation and tutorials.

The "grammar" is not trivial, but once you get a hang of it, creating graphs can be relatively painless and even enjoyable process. The docs are extremely helpful and definitely worth checking out. E.g. this one.

There is also a simplified version of the framework called "Vega Lite"


## Interactive client-side graphs on web pages with Vega

One of the most prominent use cases of Vega is the following:

* the data to be visualized is stored somewhere as `json` or `csv`, or is accessible via API
* a short, 100-200 lines long, `json` is embedded into the page
* a JavaScript runtime of Vega is loaded to your page (they provide it via CDN)
* and viola, a juicy interactive graph is there on the page

Note that in the use case above, all the heavy lifting is done by the client (a machine running your browser). Once your data is loaded, it is your PC and your PC only that is responsible for the visualization, no server involved.

## Problems scaling Vega

For reasonably sized datasets (the definition of "reasonably" is, in fact, the main question of this article) client-side "vanilla" Vega works flawlessly. However, as data starts getting big, the performance bottlenecks are becoming evident. This is not to say that Vega is not performant, but rather that any frontend-based visualization is bound to have scalability issues outside its comfort zone (in terms of dataset size).

## Purpose of this benchmark

Keeping the above in mind, I got curious how far we can actually push until it breaks (or gets unusable). Knowing some ballpark figures might help me and others to quickly get some rough idea whether client-side Vega would work for us. If it's clickable - the better.

