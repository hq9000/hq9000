---
layout: post
title: Building style-aware neural MIDI synthesizers using simplified differentiable DSP approach
permalink: /neural_synthesizers_with_simplified_ddsp.html
---

_this page is an online supplement for an article **"Building style-aware neural MIDI synthesizers using simplified differentiable DSP approach"**_

## Authors

Sergey Grechin,
Ryan Groves

[@Infinite Album](https://infinitealbum.io/)

## Talk

A talk on the [DMRN+16](https://www.qmul.ac.uk/dmrn/dmrn16/) conference:

<iframe width="1193" height="671" src="https://www.youtube.com/embed/ZpsLYAyzVx4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Here you can download the [slides (PDF)](https://github.com/hq9000/hq9000/raw/master/articles/dmrn16/DMRN%2B16%20slides.pdf) and the [abstract (PDF)](https://github.com/hq9000/hq9000/raw/master/articles/dmrn16/S.Grechin_R.Groves_DMRN%2B16_DDSP_for_MIDI_synths.pdf).

## Abstract

We explore how simplified differentiable DSP approach can be used to build realistically sounding virtual MIDI-controllable monophonic synthesizers. The simplification involves directly using  MIDI data as input to the DDSP decoder. On top of that, we show how  incorporating additional style-based and temporal channels can be used to imitate various aspects of performance and improve realism.  We further demonstrate the results of applying the approach to the task of modelling the sound of electric guitar. The presented results were obtained with a model trained on less than 12 minutes of manually MIDI-annotated audio. The source code is released along with the prepared dataset.

## Generated Audio Examples

### Example 1
![test_midi_extra_long_open_closed.mid](https://raw.githubusercontent.com/hq9000/hq9000/drmn16/articles/dmrn16/audio_examples/test_midi_extra_long_open_closed.png)

listen: [test_midi_extra_long_open_closed.mid.mp3](https://raw.githubusercontent.com/hq9000/hq9000/drmn16/articles/dmrn16/audio_examples/test_midi_extra_long_open_closed.mid.mp3)

In this example we have two long notes playing C2, the first one is "closed" and the other "open"

### Example 2
![test_midi_long_short](https://raw.githubusercontent.com/hq9000/hq9000/drmn16/articles/dmrn16/audio_examples/test_midi_long_short.png)

listen: [test_midi_long_short.mid.mp3](https://raw.githubusercontent.com/hq9000/hq9000/drmn16/articles/dmrn16/audio_examples/test_midi_long_short.mp3)

here we have a minor triad played four times, second two one octave higher. The "opennes" (CC55) is at 0 all the time

### Example 3
![test_midi_longer_open_closed](https://raw.githubusercontent.com/hq9000/hq9000/drmn16/articles/dmrn16/audio_examples/test_midi_longer_open_closed.png)

listen: [test_midi_longer_open_closed.mid.mp3](https://raw.githubusercontent.com/hq9000/hq9000/drmn16/articles/dmrn16/audio_examples/test_midi_longer_open_closed.mp3)

here we again have a minor triad played four times with longer notes, second two one octave higher. Note that the 1st and the 3rd are played with an "open" sound (CC55=127),
and the rest are played with "muted" sound
(CC55=0).

## Source Code

the source code is available on GitHub in [neural-midi-synthesizer](https://github.com/hq9000/neural-midi-synthesizer) repository.

_note:_ the repository initially started as a clone of [ddsp_simplified](https://github.com/raraz15/ddsp_simplified) repository.

## Dataset

the dataset can be downloaded from [here](https://drive.google.com/drive/folders/10wBXOffseRzjnAhv7dg6Ha71VF_t6BoJ?usp=sharing).

The dataset consists of:
- the audio in mp3 format
- annotation as a MIDI file
- Reaper project containing both audio and MIDI

### Equipment used to create the dataset

![image](https://user-images.githubusercontent.com/21345604/141061843-cea3f867-95bd-404e-a830-563f4c69ec6c.png)