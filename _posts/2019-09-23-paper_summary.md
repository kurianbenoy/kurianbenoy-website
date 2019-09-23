---
title: Speaking style adaption in text-to-speech synthesis usng sequence-to-sequence models with attention
type: post
tags:
- TTS
- Tactron 
- Lombard style
- Adaption
---

I am writing research paper in mind to build an advanced Text-to speech system for Malayalam, as a FOSS project for SMC.
I would like to thank for all the help I have recieved from [Santhosh Thottingal](https://thottingal.in/), so far and
suggesting me this project.

**Abstract**:

Currently, there are increasing interests in text-to-speech (TTS) syn-
thesis to use sequence-to-sequence models with attention. However, in challenging speaking styles, like Lombard speech,
which has higher intensity and fundamental frequency(F0) being large, cuurent approaches are not always efficent.
In this study we
propose a transfer learning method to adapt a sequence-to-sequence
based TTS system of normal speaking style to Lombard style. More-
over, we experiment with a WaveNet vocoder in synthesis of Lom-
bard speech. We conducted subjective evaluations to assess the per-
formance of the adapted TTS systems. The subjective evaluation re-
sults indicated that an adaptation system with the WaveNet vocoder
clearly outperformed the conventional deep neural network based
TTS system in synthesis of Lombard speech.

A system which was build using the Seq2Seq-TTS models and the mel-spectogram as output which employed the Wavenet
Vocoder got higher accuracy when trained with only 30 min-
utes of Lombard speech, system S5 generated synthetic speech that
was most Lombard-like among the systems compared.

The contributions of the paper are twofold. First, we develop a
speaking style adaptation system using a Seq2Seq-TTS model. Sec-
ond, we study the use of a WaveNet vocoder for the application
of Lombard speech synthesis. To the best of our knowledge, the cur-
rent study is the first investigation on speaking style adaptation of
speech synthesis using a modern Seq2Seq-TTS system.

 
**SEQ2SEQ-TTS System**

Despite promising results in synthetic speech using Statistic parametric speech synthesis.
These models depend heavily on encoder-decoder neural network
structures that map a sequence of characters to a sequence of acous-
tic frames. These models combine the front-end and back-end and
learn relations between them from data only. When sequence-to-
sequence models are coupled with neural vocoders, they enable
generating raw waveforms directly from text. It was
demonstrated that state-of-the-art results in TTS can be achieved
with the sequence-to-sequence technology.

The model accepts
either mono-phonemes or graphemes as inputs and emits acoustic
parameters as outputs. It consists of three main components: 1) en-
coder, 2) attention, and 3) decoder. The encoder takes text sequence
x of length L as input, which represented either in the character or
phoneme domain as one-hot vectors. The encoder learns a continu-
ous sequential representation h using various neural network archi-
tectures such as LSTMs and/or CNNs.

```
h = encoder(x)

αt = attention(st−1 , αt−1 , h)

ct = sum of(αt, ht)

yt = decoder(st−1 , ct )
Equations in paper to fear you
```
where st−1 is the (t − 1)-th state of the decoder recurrent neural
network and αt ∈ RL are the attention weights or the alignment and
ct is the context or attention vector. The decoder takes the previous
hidden state st−1 and the current context vector ct as inputs and
generates the current output yt . This process runs until the end of
the utterance is reached

**Adaption of Seq2Seq models**

### Experiments mentioned in the model



**Conclusion**

This paper compared different TTS models and vocoders to adapt
the speaking style of speech synthesis from normal to Lombard.
The study proposes using an adaptation method based on fine-tuning
combined with sequence-to-sequence based TTS models and the
WaveNet vocoder conditioned using mel-spectrograms. Listening
tests show that the proposed method outperformed the previous best
method that was developed using a LSTM-RNN based adapted sys-
tem. Future work includes an extensive subjective evaluations and
training both the WaveNet and Seq2Seq-TTS model in a single
pipeline.


