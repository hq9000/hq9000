---
layout: post
title: "A/B testing in Reaper with SwixMitch - an easy way to do a reality check when mixing and mastering."
---

When you work on a track for a long time, it's virtually impossible to maintain an accurate judgement of your material. Is it loud enough? Too bright? To quiet?

After listening to a track for hours, I am sure it is not easy for you as well to confidently answer such questions.

They say it helps to do a so called A/B comparison with a reference. I.e. have a reference track, yours or someone else's, that you want your track to sound comparable with. And it's indeed a very useful method do quickly see how your mix sounds next to some reference one.

I do it in Reaper the following way:

- let's assume we are working on a stereo mix - the muster track has, therefore, two channels
- we make it 4 channels!
- then we create a "reference" track and drop some mp3/wav file there (this would be our reference)
- we target this reference track to channels 3/4 of the master.
- on master, we put an instance of a little stock JS plugin called **SwixMitch**
- we set it up so that "A" corresponds to channel 1/2 and "B" to channel 3/4.
- now essentially we have a crossfader, which in position A gives you your mix, and in B - the reference
- now by moving the toggle left and right with a mouse, we can smoothly transit between source, and this is how our deviations from reference become very easy to see.

Bonus tip: if you put an instance of meter plugin (such as JS Loudness Meter) after SwixMitch, you will be able to compare quantifiable parameters of your mix such as LUFS and RMS.

Now a few screenshots:

<img width="488" height="205" alt="Image" src="https://github.com/user-attachments/assets/22a35023-6fb3-4744-99a0-80572eda5242" />

<img width="1835" height="368" alt="Image" src="https://github.com/user-attachments/assets/4a6ff81c-3b32-400d-b2a1-3370b907257f" />


