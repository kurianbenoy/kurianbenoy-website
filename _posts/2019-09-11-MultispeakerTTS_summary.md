---
title: Research paper- Transfer Learning from Speaker Verification to Multispeaker Text-To-Speech Synthesis
author: Kurian Benoy
type: post
tags:
- audio
- Deep learning
- Text To Speech Synthesis
---
## Introduction

In this paper we discuss about neural network-based system for Text to Speech(TTS) synthesis that can generate speech
audio in the voice of different speakers, including those unseen during training. This research paper was presented
during 32nd conference of NeurIPS 2018, Montreal, Canada and is authored by researchers from Google Inc.

The goal of this work is to build a TTS system which can generate natural speech for a variety of speakers in a data
efficent manner. We specifically address a zero-shot type learning system, where a speakers cloned audio can be
generated for any speech on getting few seconds of untranscribed reference audio.

Here the approach is to decouple speaker modelling from speech synthesis by independently training a
speaker-discriminative network that captures charteristics from small amount of speaker audio data.

// talk about tacktron2, previous inventions, etc

## Multispeaker speach synthesis model

Our system is composed of three independently trained neural networks:

1. A *recurrent speaker encoder* which computes a fixed dimensional vector from a speech signal.

2. *Sequence-to-sequence synthesizer* which predicts a mel spectrogram from a sequence of grapheme inputs, conditioned
on speaker emedding vector.

3. An autoregressive *Wavenet vocoder*, which converts the spectogram into time domain waveforms.

### Speaker Encoder

It is used to condition the synthesis network on reference speech signal from the desired target speaker. It is critical
for capturing the crucial characteristics of different speaker and identify the phonetic signal, background noise.

<copy>

### Synthesizer

The synthesizer is trained to convert a sequnce of phoneme or graheme sequence(the text or audio) and is converted into
log-mel spectograms, which are commonly used in Audio applications of Deep learning. The Tactron2 architecture to
support multiple speakers is extended to recurrent sequence-to-sequence with attention.

An embedding vector for the target speaker is concatenated with synthesizer encoder output at each step, thus passing
embeeding to the attention layer converges across different speakers.The predicted mel spectrogram by synthesizer
captures all the relevant details needed for higly qualidy synthesis of various voices.

<copy>

### Neural Vocoder

The Wavenet acts as a vocoder to invert the synthesized mel spectrograms emitted by the synthesis network into
time-domain waveforms, ie the final voice you are hearning. Wavent architecture is composed of 30 dilated convolution
layers. The network is not directly conditioned on the output of the speaker encoder.

### Interference and zero-shot speaker adaption

In practise we find that using a single audio clip of a few sconds duration is sufficent to synthesize new speech with
the corresponding speaker characteristics, representing zero-shot adaption to novel speakers.

Surprising the results on interference of male and female show some characteristics like strongly pitched voice of men's
voice while females voice are found to be having larger speaking rate for a embedded voice.

## Experiments

The google team performed extensive reseach and trained the speaker encoder on a properietary voice seach corpus engine
containing 36M utterances and compared resuults two public datasets for speech syntesis and vocoder networks.
a) VCTK - contains 44 hours of clean speech from 109 speakers
b) LibriSpeech - contains 436 hours of speech from 1172 speakers.

The model performed really well, yet not reached the human level of intellgences which is measured in Mean Opinion
score(MOS).

They compared the architecture based on the following parameters:
- Speech Naturalness
- Speaker similarity
- Speaker verification
- Speaker embedding space
- Number of speaker encoder training speakers
- Fictious speakers

Detailed results can be found within [the paper]().

## Conclusion

blah ....
