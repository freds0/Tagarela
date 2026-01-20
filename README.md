# TAGARELA Dataset

**A Large-Scale Portuguese Speech Dataset from Podcasts**

[Web Page](https://freds0.github.io/Tagarela/)

TAGARELA (/ta.ga.ˈRE.la/) is a large-scale Portuguese speech dataset curated from the "Cem Mil Podcasts" collection, designed for training automatic speech recognition (ASR) and text-to-speech (TTS) models.

## Dataset Statistics

| Metric | Value |
|--------|-------|
| Total Hours | 8,972+ |
| Podcast Episodes | 16,806 |
| Podcast Shows | 2,094 |
| Distinct Speakers | ~13,368 |

### Dialect Distribution

- **Brazilian Portuguese (pt-BR):** 8,130 hours (91%)
- **European Portuguese (pt-PT):** 842 hours (9%)

### Gender Distribution

- **Male speakers:** 6,368 hours (70%)
- **Female speakers:** 2,604 hours (30%)

### Segment Statistics

- **Average duration:** 9.30 ± 5.49 seconds
- **Average words per segment:** 27.69 ± 17.06 words

## Dataset Subsets

### Full Subset (8,972 hours)
Includes audio containing various types of disfluencies, designed for robust **automatic speech recognition (ASR)** training.

### Clean-Speech Subset (2,800 hours)
A curated speech-only subset designed for high-quality **text-to-speech (TTS)** and speech generation tasks.

## Processing Pipeline

The dataset was created through a comprehensive multi-stage pipeline:

1. **Audio Standardization** - FLAC format, 16kHz, 16-bit, mono
2. **Segmentation** - 5-20 second clips at natural silence points
3. **Speaker Diarization** - Using pyannote framework
4. **Overlapping Speech Detection** - Wav2vec2-XLS-R classifier
5. **Transcription Generation** - Bootstrap strategy (ElevenLabs Scribe + fine-tuned Whisper large-v3)
6. **Quality Enhancement** - Vocos vocoder as denoiser

## Benchmark Results

### ASR (Common Voice 17.0 pt test set)

| Model | WER (%) |
|-------|---------|
| Canary-1B-Flash | **7.8** |
| Distil-Whisper | 9.2 |
| Parakeet TDT | 12.3 |

### TTS (2,800h clean-speech subset)

| Model | CER (%) | WER (%) | MOS |
|-------|---------|---------|-----|
| Orpheus-TTS | **19.32** | **26.81** | 4.00 |
| Chatterbox | 23.73 | 31.50 | **4.53** |

## Citation

If you use the TAGARELA dataset in your research, please cite:

```bibtex
@inproceedings{oliveira2026tagarela,
  title={TAGARELA - A Portuguese Speech Dataset from Podcasts},
  author={Oliveira, Frederico Santos de and Gris, Lucas Rafael Stefanel and
          Ferreira, Alef Iury Siqueira and Rosa, Augusto Seben da and
          Ferro Filho, Alexandre Costa and Casanova, Edresson and
          Shulby, Christopher Dane and Sousa, Rafael Teixeira and
          Silva, Diogo Fernandes Costa and Soares, Anderson da Silva and
          Galv{\~a}o Filho, Arlindo Rodrigues},
  booktitle={IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP)},
  year={2026}
}
```

## Authors

- **Frederico Santos de Oliveira** - Federal University of Mato Grosso (UFMT)
- **Lucas Rafael Stefanel Gris** - Federal University of Goias (UFG)
- **Alef Iury Siqueira Ferreira** - Federal University of Goias (UFG)
- **Augusto Seben da Rosa** - Paulista State University (UNESP)
- **Alexandre Costa Ferro Filho** - Federal University of Goias (UFG)
- **Edresson Casanova** - NVIDIA
- **Christopher Dane Shulby** - Elsa Speak
- **Rafael Teixeira Sousa** - Federal University of Mato Grosso (UFMT)
- **Diogo Fernandes Costa Silva** - Federal University of Goias (UFG)
- **Anderson da Silva Soares** - Federal University of Goias (UFG)
- **Arlindo Rodrigues Galvão Filho** - Federal University of Goias (UFG)

## Acknowledgements

This work has been fully funded by the project *Research and Development of Algorithms for Construction of Digital Human Technological Components* supported by the **Advanced Knowledge Center in Immersive Technologies (AKCIT)** in partnership with the Federal University of Goiás (UFG).

## License

Please refer to the dataset documentation for licensing information.
