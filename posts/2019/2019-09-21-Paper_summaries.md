---
aliases:
- /Audio/Final Year projects/TTS/Wavenet/2019/09/21/Paper_summaries
categories:
- Final Year projects
- TTS
- Wavenet
- Audio
date: '2019-09-21'
layout: post
title: Literature review for my project

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

**Background**

Text to Speech TTS [1, 16, 19, 20, 24], which aims to synthesize natural and intelligible speech
given text, has long been a hot research topic in the field of artificial intelligence. The research on
TTS has shifted from early concatenative synthesis [9], statistical parametric synthesis [12, 25] to
neural network based parametric synthesis [1] and end-to-end models [13, 16, 20, 24], and the quality
of the synthesized speech by end-to-end models is close to human parity. Neural network based
end-to-end TTS models usually first convert the text to acoustic features (e.g., mel-spectrograms) and
then transform mel-spectrograms into audio samples. However, most neural TTS systems generate
mel-spectrograms autoregressively, which suffers from slow inference speed, and synthesized speech
usually lacks of robustness (word skipping and repeating) and controllability (voice speed or prosody
control). In this work, we propose FastSpeech to generate mel-spectrograms non-autoregressively,
which sufficiently handles the above problems.

Sequence to Sequence Learning Sequence to sequence learning [2, 4, 22] is usually built on the
encoder-decoder framework: The encoder takes the source sequence as input and generates a set of
representations. After that, the decoder estimates the conditional probability of each target element
given the source representations and its preceding elements. The attention mechanism [2] is further
introduced between the encoder and decoder in order to find which source representations to focus
on when predicting the current element, and is an important component for sequence to sequence
learning.
In this work, instead of using the conventional encoder-attention-decoder framework for sequence to
sequence learning, we propose a feed-forward network to generate a sequence in parallel.

**Fast Speech Architecture:**

In this section, we introduce the architecture design of FastSpeech. To generate a target mel-
spectrogram sequence in parallel, we design a novel feed-forward structure, instead of using the
encoder-attention-decoder based architecture as adopted by most sequence to sequence based autore-
gressive [13, 20, 22] and non-autoregressive [7, 8, 23] generation. The overall model architecture of
FastSpeech is shown:

a) FeedForward Transformer
b) Length Regulator
c) Duration Predictor

The architecture for FastSpeech is a feed-forward structure based on self-attention in Transformer [22]
and 1D convolution [5, 17]. We call this structure as Feed-Forward Transformer (FFT), as shown in
Figure 1a. Feed-Forward Transformer stacks multiple FFT blocks for phoneme to mel-spectrogram
transformation, with N blocks on the phoneme side, and N blocks on the mel-spectrogram side, with
a length regulator (which will be described in the next subsection) in between to bridge the length gap
between the phoneme and mel-spectrogram sequence. Each FFT block consists of a self-attention and
1D convolutional network, as shown in Figure 1b. The self-attention network consists of a multi-head
attention to extract the cross-position information. Different from the 2-layer dense network in
Transformer, we use a 2-layer 1D convolutional network with ReLU activation. The motivation is that
the adjacent hidden states are more closely related in the character/phoneme and mel-spectrogram
sequence in speech tasks. We evaluate the effectiveness of the 1D convolutional network in the
experimental section. Following Transformer [22], residual connections, layer normalization, and
dropout are added after the self-attention network and 1D convolutional network respectively.

The length regulator (Figure 1c) is used to solve the problem of length mismatch between the phoneme
and spectrogram sequence in the Feed-Forward Transformer, as well as to control the voice speed and
part of prosody. The length of a phoneme sequence is usually smaller than that of its mel-spectrogram
sequence, and each phoneme corresponds to several mel-spectrograms. We refer to the length of
the mel-spectrograms that corresponds to a phoneme as the phoneme duration (we will describe
how to predict phoneme duration in the next subsection). Based on the phoneme duration d, the
length regulator expands the hidden states of the phoneme sequence d times, and then the total length
of the hidden states equals the length of the mel-spectrograms.

Phoneme duration prediction is important for the length regulator. As shown in Figure 1d, the **duration
predictor** consists of a 2-layer 1D convolutional network with ReLU activation, each followed by
the layer normalization and the dropout layer, and an extra linear layer to output a scalar, which
is exactly the predicted phoneme duration. Note that this module is stacked on top of the FFT
blocks on the phoneme side and is jointly trained with the FastSpeech model to predict the length of
mel-spectrograms for each phoneme with the mean square error (MSE) loss. 
