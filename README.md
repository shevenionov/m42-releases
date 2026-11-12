# M42 releases

Downloads for M42, a Mac app for collecting visual references.

This repository holds only what the app downloads or what you install: builds of the app, and the model
it uses for search. The app's source is not here.

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
