_online supplement page for an article **Building style-aware neural MIDI synthesizers using simplified differentiable DSP approach**"_

## Abstract
We explore how simplified differentiable DSP approach can be used to build realistically sounding virtual MIDI-controllable monophonic synthesizers. The simplification involves directly using  MIDI data as input to the DDSP decoder. On top of that, we show how  incorporating additional style-based and temporal channels can be used to imitate various aspects of performance and improve realism.  We further demonstrate the results of applying the approach to the task of modelling the sound of electric guitar. The presented results were obtained with a model trained on less than 12 minutes of manually MIDI-annotated audio. The source code is released along with the prepared dataset.

The full text of the article is available [here](https://todo.com).

[here]: http://todo.com

## Audio Examples

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

listen: [test_midi_longer_open_closed.mid.mp3](https://raw.githubusercontent.com/hq9000/hq9000/drmn16/articles/dmrn16/audio_examples/test_midi_longer_open_closed_short.mp3)

here we again have a minor triad played four times with longer notes, second two one octave higher. Note that the 1st and the 3rd are played with an "open" sound (CC55=127) and 
the reset are played with "muted" sound (CC55=0)

## Source Code

the source code is available on GitHub in [neural-midi-synthesizer](https://github.com/hq9000/neural-midi-synthesizer) repository.

_note:_ the repository initially started as a clone of [ddsp_simplified](https://github.com/raraz15/ddsp_simplified) repository.

## Dataset

the dataset can be downloaded from [here](https://drive.google.com/drive/folders/10wBXOffseRzjnAhv7dg6Ha71VF_t6BoJ?usp=sharing).

The dataset consists of:
- the audio in mp3 format
- annotation as a MIDI file
- Reaper project containing both audio and MIDI