# M42 releases

Downloads for M42, a Mac app for collecting visual references.

This repository holds only what the app downloads or what you install: builds of the app, and the model
it uses for search. The app's source is not here.

## Download

**[Download M42 for Mac](https://github.com/shevenionov/m42-releases/releases/latest/download/M42.dmg)**

Open the disk image and drag M42 into Applications. It needs macOS 27 or later.

M42 keeps itself up to date: it checks here for newer builds and offers to install them. To check right
away, choose M42 ▸ Check for Updates…. Every build is listed under
[Releases](https://github.com/shevenionov/m42-releases/releases); the ones named `M42 …` are the app.

## Search model

M42 searches by what a reference shows ("mountains", "similar to this") with a model that runs on your
Mac. Nothing is sent anywhere to be searched.

The model is [SigLIP 2](https://huggingface.co/google/siglip2-base-patch16-256) (base, patch 16, 256 px)
by Google, converted to Core ML and compressed for Apple hardware:

- the image half uses 8-bit palettes, the text half 6-bit palettes;
- the vocabulary table is stored as a separate file of 8-bit rows;
- the tokenizer is repacked into a compact binary file.

M42 downloads it once, on first launch. The releases named `search-model-N` each carry one file,
`m42-search-model-N.zip`.

SigLIP 2 is licensed under the Apache License 2.0, and so is this converted copy: see
[LICENSE-search-model.txt](LICENSE-search-model.txt). The original weights are Google's; the changes
listed above are M42's.

## ffmpeg

M42 can save the video behind a pasted link. The tools that do that are not part of the app; it asks
first, then downloads them. Two come straight from their makers ([yt-dlp](https://github.com/yt-dlp/yt-dlp)
and [Deno](https://github.com/denoland/deno)). The third is here: the releases named `ffmpeg-N` each carry
one file, `m42-ffmpeg-N.zip`.

It is [FFmpeg](https://ffmpeg.org), unmodified, compiled for Apple silicon Macs with only the parts M42
uses (joining a video's picture and sound into one file). It is licensed under the GNU Lesser General
Public License, version 2.1 or later. Each zip contains the licence and a note with the address and
checksum of the source it was built from and the options it was configured with; the same is in each
release's description.
