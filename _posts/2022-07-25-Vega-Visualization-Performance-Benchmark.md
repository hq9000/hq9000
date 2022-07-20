## Abstract (TLDR)

Vega is a visualisation grammar (a language) and a runtime for server- and client-side visualizations. A live benchmark showing client-side performance of Vega on differently sized datasets is presented. Vega is shown to scale well to up to 5k datapoints. A survey on possible ways to overcome scaling issues is provided.

![image](https://user-images.githubusercontent.com/21345604/179940839-b9866534-9016-4f0c-a607-d9fc02badbd2.png)

## What is Vega

Vega is a "visualization grammar", essentially, a specification language and a JavaScript library to interpret it (both in browser and server-side). Vega allows to create interactive graphs, called "visualizations", in a declarative way. Declarative here means requiring no coding in traditional sense, we only write a JSON specification. 

Vega is widely used in scientific and business circles and has a thriving community, great documentation and tutorials.

The "grammar" is far from trivial, but once you get a hang of it, creating graphs can be relatively painless and even enjoyable process. The docs are extremely helpful and definitely worth checking out. 
There is also a simplified version of the framework called "Vega Lite"


## Interactive client-side graphs on web pages with Vega

One of the most prominent use cases of Vega is the following:

* the data to be visualized is stored somewhere as `json` or `csv`
* a short, 100-200 lines long, `json` is embedded into the page
* a JavaScript runtime of Vega is loaded to your page (they provide it via CDN)
* and viola, a juicy interactive graph is there on the page

Note that in the use case above, all the heavy lifting is done by the client (a machine running your browser). Once your data and visualization specification are loaded to the browser, it is your PC and your PC only that is responsible for the visualization, no server involved.

## Problems scaling Vega

For reasonably sized datasets (the definition of "reasonably" is, in fact, the main question of this article) client-side Vega works flawlessly. However, as data starts getting big, the performance bottlenecks are becoming evident. This is not to say that Vega is not performant, but rather that any frontend-based visualization is bound to have scalability issues outside its comfort zone (in terms of dataset size).

## Purpose of this benchmark

Keeping the above in mind, I got curious about how far we can actually push it until it breaks or gets unusable. Knowing some ballpark figures might help me and others to quickly get some rough idea whether client-side Vega would work for us. 

## Purpose of this benchmark