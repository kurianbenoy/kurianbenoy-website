---
title: Vegam Whisper Family of Models and demoing Malayalam Speech to Text
author: Kurian Benoy
date: 2023-06-11
date-format: full
categories: [academia, life, conference, Malayalam, Audio]
subtitle: Demo Presentation session presented at Summit 23, IIIT Kottayam
toc: true
---

![](../../../talks/iiit-kottayam-summit/huggingface.png)

## Links

- [Slides](../../../talks/iiit-kottayam-summit/demo.qmd)
- [Pallakku a Malayalam speech to text demo](https://huggingface.co/spaces/kurianbenoy/Pallakku)
- Venue: AA 127, IIIT Kottayam.

## Vegam Whisper Family of Models

Inspired by [faster-whisper](https://github.com/guillaumekln/faster-whisper) which is a 
reimplementation of OpenAI’s Whisper model using CTranslate2 speeds upto 4 times faster
than `openai/whisper` for the same accuracy while using less memory.

CTranslate2 supports various quantization formats and we have trained models for the following
quantization formats:

- float16
- int16
- float8
- int8_float8
- No quantization

For Malayalam, I used the best model in my benchmarking study ie [thennal/whisper-medium-ml](https://huggingface.co/thennal/whisper-medium-ml) and converted into all possible quantization weights.

1. [kurianbenoy/vegam-whisper-medium-ml](https://huggingface.co/kurianbenoy/vegam-whisper-medium-ml)
2. [kurianbenoy/vegam-whisper-medium-ml-fp16](https://huggingface.co/kurianbenoy/vegam-whisper-medium-ml-fp16)
3. [kurianbenoy/vegam-whisper-medium-ml-int16](https://huggingface.co/kurianbenoy/vegam-whisper-medium-ml-int16)
4. [kurianbenoy/vegam-whisper-medium-ml-fp8](https://huggingface.co/kurianbenoy/vegam-whisper-medium-ml-fp8)
5. [kurianbenoy/vegam-whisper-medium-ml-int8_float8](https://huggingface.co/kurianbenoy/vegam-whisper-medium-ml-int8_float8)

## Code to run faster-whisper code

![Source Code](../../../talks/iiit-kottayam-summit/faster-whisper.png)

## Demo Video -1 and it's associated Output

{{< video https://www.youtube.com/embed/zm1gU8hRHxA >}}

> Oru Thai Nadam sang by Venugopal and Sreya, Lyrics by Sugathakumari

![Output of clip from Video 1](../../../talks/iiit-kottayam-summit/25s_audio.png)

## Demo Video -2 and it's associated Output

{{< video https://www.youtube.com/embed/fZZFCOkWquY >}}

> Sang by Sithara Krishna Kumar, Lyrics by BK Hari Narayanan. This was a song created spontaneously at MBIFL 2023


![Output of clip from Video 2](../../../talks/iiit-kottayam-summit/10s_audio.png)

## Pallakku

- Pallakku is a Malayalam speech to text demo leveraging the model-weights of whisper family
of models. It might be the first huggingface 🤗 spaces for Malayalam speech to text.

Two options to try it out:

1. [🤗 spaces](https://huggingface.co/spaces/kurianbenoy/Pallakku)

![](../../../talks/delft-fastai/pallakku.png)

You can try it out in [the below link](https://huggingface.co/spaces/kurianbenoy/Pallakku).

2. GPU-based microservice (coming soon.)

## What is behind the name of Vegam and Pallakku?

- Vegam is a Malayalam word which means speed.
- Pallakku is a Malayalam word which means a palanquin. It is a vehicle which is carried by people.

As an author of these work, I just wanted to say the meaning of these words
doesn't really have anything to do with the package. Vegam might not be the
fastest Malayalam ASR model and Pallakku is named not to refer to the old
colonial times. I just named it for the sake of naming it.

## Thanks to

- [Santhosh Thottingal](https://twitter.com/santhoshtr/) for his support and guidance. Santhosh
told me about faster-whisper and the utility to convert the model weights to various quantization formats.
- Organizers of IIIT Summit 23 for giving me an opportunity to present my work.

I am really happy to receive lot of curious questions from all who came to visit
my demo stall like some professors who taught me in previous semesters like Dr. Keshab Nath etc.
and some of Btech students.
