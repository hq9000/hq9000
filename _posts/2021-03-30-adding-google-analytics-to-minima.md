
update 2024-02-17: After working fine, it broke. The stats stopped being gathered. The reason is breaking migration, in 2023, I guess, of Google Analytics to newer tag format.

To fix things, you just need to put the tracking html code file in `_includes/google-analytics.html`.

The tracking code looks something like this:
```
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-J900LXB0C2"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-J900LXB0C2');
</script>
```
This code you get from your google analytics property, look for tagging instructions. It must be easy to find.

Instead of explaining it further, let me just point you to the [this commit that fixed it for this site](https://github.com/hq9000/hq9000/commit/1b1f0578e6343b730cbd550c78f072deb49411e5).

Please note that you need both: the file in `_includes` and a line in `_config.yaml`.


## Outdated way (not working) left for history

**Update 2024-02-17: ignore the stuff below, it no longer works:**

It has turned out to be ridiculously easy to add a google analytics tag to my blog. So easy that it actually deserves to be the first blog post.

I'm using a very standard and recommended github pages setup with `jekyll` running with the default `minima` theme.

In my case, all I had to do was adding this line:

```
google_analytics: XXXXXX
```

into `_config.yml`, where XXXXX is my tracking code. [See it here](https://github.com/hq9000/hq9000/blob/6164401661334373e9584e5524bd38b8400c7183/_config.yml#L28) 

The hardest part was actually to find that tracking code in my GA account. In the end, I found it in "Admin" area, where it's called `Measurement ID`:

![image](https://user-images.githubusercontent.com/21345604/112961116-bd567000-914d-11eb-90ec-4b55642bc714.png)

