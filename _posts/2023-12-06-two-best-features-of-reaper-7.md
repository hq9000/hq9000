---
title: The two features of Reaper 7 I like the most
---

Having started using Reaper around 2008, I can safely consider myself not a beginner.
With some back and forth, having done detours to Cakewalk Sonar, Cubase and Ableton Live (not to mention relict trackers such as Fast Tracker and Buzz in the 90s), I have finally decided to stick
to this wonderfully powerful, albeit not exactly the beginner-friendliest and slicky looking, DAW. 

I would say this
Reaper perfectly fits the nerdy part of me, and fully satisfies my willingness to invest into the tools of my choice.

Recently, the 7th version of Reaper came out. Surely not a groundbreaking update, if you ask me, and I'd not have even noticed any major changes at first. As a software guy, I dread upgrades, and initially I didn't feel that it was worth it. In this case, however, I took the time to actually read the [release notes](https://dlz.reaper.fm/userguide/WhatsNewReaper7Summary_r2.pdf) highlighting the changes.

What I found was a couple of features I personally found really great, one purely visual and the other more on the routing side.

## Greatest feature of Reaper 7 #1: Track delimiters

You can add non-collapsible "Visual spacers" between tracks, like this

![image](https://github.com/hq9000/hq9000/assets/21345604/f3d54336-76a2-4176-af3b-bd5d5ed2a1e1)

I can see it rather useful to add a bit of more organization to your tracks while avoiding track nesting which complicates the routing and adds quite a bit of clutter. Simple and useful feature!

Yes, these delimiters stay 16 pixels high when you zoom! The exact size is configurable somewhere in the settings, but the default 16 pixels seek t0 work great for me.

## Greatest feature of Reaper 7 #2: "Container" plugins + parallel processing

If you ever encountered the concept of subchains i Ableton Live great and missed that part in Reaper (for drum kits or synth layering), there is really good news for you.

Previously fully sequential, with Reaper 7 you can have parallel processing with subchains within one track.

For comparison, this is how I'd do that in Live, with so called "Instrument Rack". In the screenshot below, there is a track that has two Synth1 instances working in parallel, one of which is processed with an equalizer:

![image](https://github.com/hq9000/hq9000/assets/21345604/369b21d7-a7d4-4e92-9d20-76ddfd946c48)

Note how nicely I can adjust volume/pan of the subchannels, solo and mute them and so on. Great feature and something that I secretly missed in my favorite DAW (Reaper, that is).

The good news is that you can do something like this in Reaper.  The appearance of it is honestly not great and it's not nearly as user-friendly as the one in Ableton Live, but it does the thing. Let's replicate the same setup in Reaper:

![image](https://github.com/hq9000/hq9000/assets/21345604/a04524bd-145e-42a1-b690-75d674e0508c)

The key is is use a "Container", which is basically... well... a container that gives you a nested chain with the similar UI.

And then also you need to make it processed "in parallel with previous FX" that adds those two weird pipes before its name: `||`:

![image](https://github.com/hq9000/hq9000/assets/21345604/dc880039-7c27-46f0-b3cf-7ca016c634fb)

Sure, nothing of that impossible before, you would just have to add more and more tracks and submixes, carefully routing Audio/Midi and doing quite a lot of clicks and complicating the mental model of your project. I've been there many times.

So, a great feature, and long awaited too! I am already using it for synth layering!

What I do still miss, though, is:
-  always visible visual signal indication on per-chain basis
- ability to adjust volume/panning for subchains
- soloing the chain (muting is simple by disabling the corresponding subchain, no problem there)

Let's hope the developers address this in some upcoming release which I definitely be looking forward to.

Thanks for reading and happy Reaper hours!

>_By the way, if are you a musician looking for collaboration, be invited to drop me a line at grechin.sergey(at)gmail.com! Be you a producer, vocalist, songwriter, let's see what we can do together! Something to consider would be: checking our productions to help detect mixing glitches (have another pair of ears), mastering of our tracks and up to releasing something together._

