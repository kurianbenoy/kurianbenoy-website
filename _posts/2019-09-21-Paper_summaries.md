---
title: Literature review for my project
type: post
tags:
- Final Year projects
- TTS
- Wavenet
- Audio
---

## Speaking style adaption in text-to-speech synthesis usng sequence-to-sequence models with attention

**Abstract**:

Currently, there are increasing interests in text-to-speech (TTS) syn-
thesis to use sequence-to-sequence models with attention. These
models are end-to-end meaning that they learn both co-articulation
and duration properties directly from text and speech. Since these
models are entirely data-driven, they need large amounts of data
to generate synthetic speech with good quality. However, in chal-
lenging speaking styles, such as Lombard speech, it is difficult to
record sufficiently large speech corpora. Therefore, in this study we
propose a transfer learning method to adapt a sequence-to-sequence
based TTS system of normal speaking style to Lombard style. More-
over, we experiment with a WaveNet vocoder in synthesis of Lom-
bard speech. We conducted subjective evaluations to assess the per-
formance of the adapted TTS systems. The subjective evaluation re-
sults indicated that an adaptation system with the WaveNet vocoder
clearly outperformed the conventional deep neural network based
TTS system in synthesis of Lombard speech.

The results of the style similarity test are plotted in Figure 4. From
the right pane of the figure, it can be observed that synthesized
speech by all adapted systems were rated to sound different from
natural normal speech with high confidence. When compared to the
natural Lombard reference (left pane), system S5 was rated highest,
followed by systems S3, S4, S2, and S1. System S5 was built us-
ing the Seq2Seq-TTS model and the mel-spectrogram as output. It
can be clearly seen that those systems that employed the WaveNet
vocoder got higher scores than the ones that used the more tradi-
tional World vocoder. Further, system S5, which is based on con-
ditioning the WaveNet vocoder with mel-spectrograms, got a higher
score than the ones that used the World vocoder, confirming the find-
ings made in a earlier study [33]. From this results we can conclude
that even though we trained the WaveNet vocoder with only 30 min-
utes of Lombard speech, system S5 generated synthetic speech that
was most Lombard-like among the systems compared.

**COnclusion**

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

## FastSpeech: Fast, Robust and Controllable speech

**Abstract**
Neural network based end-to-end text to speech (TTS) has significantly improved
the quality of synthesized speech. Prominent methods (e.g., Tacotron 2) usually
first generate mel-spectrogram from text, and then synthesize speech from the
mel-spectrogram using vocoder such as WaveNet. Compared with traditional
concatenative and statistical parametric approaches, neural network based end-
to-end models suffer from slow inference speed, and the synthesized speech is
usually not robust (i.e., some words are skipped or repeated) and lack of con-
trollability (voice speed or prosody control). In this work, we propose a novel
feed-forward network based on Transformer to generate mel-spectrogram in paral-
lel for TTS. Specifically, we extract attention alignments from an encoder-decoder
based teacher model for phoneme duration prediction, which is used by a length
regulator to expand the source phoneme sequence to match the length of the target
mel-spectrogram sequence for parallel mel-spectrogram generation. Experiments
on the LJSpeech dataset show that our parallel model matches autoregressive mod-
els in terms of speech quality, nearly eliminates the problem of word skipping and
repeating in particularly hard cases, and can adjust voice speed smoothly. Most
importantly, compared with autoregressive Transformer TTS, our model speeds up
mel-spectrogram generation by 270x and the end-to-end speech synthesis by 38x.
Therefore, we call our model FastSpeech. We will release the code on Github.3

