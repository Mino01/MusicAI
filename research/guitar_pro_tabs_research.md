# Guitar Pro Tabs Generation Research

## Phase 1: Audio-to-MIDI Transcription Technologies

### 1. Spotify Basic Pitch
- **URL**: https://github.com/spotify/basic-pitch
- **License**: Apache 2.0
- **Key Features**:
  - Polyphonic + instrument-agnostic transcription
  - Pitch bend detection (vibrato, glissando, slides)
  - Lightweight model (<20 MB)
  - Faster than real-time on most computers
  - Works with piano, guitar, voice, and other instruments
- **Technical Approach**:
  - Uses harmonic constant-Q transform as input
  - Jointly models onsets, frames, and multipitch information
  - Shallow architecture with fewer layers/parameters
- **Output**: MIDI with note events and pitch bends

### 2. NeuralNote
- **URL**: https://github.com/DamRsn/NeuralNote
- **Type**: Audio plugin (VST/AU)
- **Features**:
  - Real-time audio to MIDI conversion
  - Works within DAWs (Digital Audio Workstations)
  - Deep learning based

### 3. Klangio
- **URL**: https://klang.io/
- **Type**: Commercial AI service
- **Output Formats**: Sheet Music, MIDI, MusicXML

### 4. Academic Research
- "Automatic Music Transcription using CNN" (Telila, 2022)
- "Onsets and Frames: Dual-Objective Piano Transcription" (Hawthorne et al., 2018)
- Stanford CS230 AMT projects using Transformer models

## Key Challenges in Audio-to-MIDI Transcription

1. **Polyphonic Untangling**: When multiple notes overlap in time and frequency
2. **Note Segmentation**: Determining when to group pitches into single notes vs. multiple notes
3. **Instrument Generalization**: Making models work across different instruments
4. **Expressive Elements**: Capturing pitch bends, vibrato, slides

## Next Steps
- Research Guitar Pro file format (.gp, .gp5, .gpx)
- Research MIDI-to-tablature conversion
- Research open-source Guitar Pro libraries


## Phase 2: Guitar Pro File Format and Generation Libraries

### Guitar Pro File Formats

| Format | Extension | Description |
|--------|-----------|-------------|
| Guitar Pro 3-5 | `.gp3`, `.gp4`, `.gp5` | Proprietary binary format from Arobas Music |
| Guitar Pro 6 | `.gpx` | Proprietary archive format storing music as XML |
| Guitar Pro 7+ | `.gp` | ZIP archive storing music information as XML |

### Key Libraries for Guitar Pro File Handling

#### 1. PyGuitarPro (Python)
- **Repository**: https://github.com/Perlence/PyGuitarPro
- **License**: LGPL-3.0
- **Capabilities**: Read/write GP3, GP4, GP5 files
- **Note**: Version 0.6 required for DadaGP compatibility

#### 2. AlphaTab (JavaScript/.NET/Android)
- **Website**: https://alphatab.net/
- **Repository**: https://github.com/CoderLine/alphaTab
- **License**: MPL-2.0
- **Capabilities**:
  - Load Guitar Pro 3-8, MusicXML, CapXML, AlphaTex
  - Render music notation and tablature
  - Audio playback with MIDI synthesizer
  - Cross-platform (Web, .NET, Android)

#### 3. TuxGuitar (Java)
- **Website**: https://tuxguitar.app/
- **Repository**: https://github.com/helge17/tuxguitar
- **License**: LGPL
- **Capabilities**: Open-source tablature editor supporting GP, PowerTab, TablEdit, MIDI

### DadaGP Dataset
- **Repository**: https://github.com/dada-bots/dadaGP
- **Size**: 26,181 GuitarPro songs in 739 genres
- **Format**: Token sequence format for GPT2, TransformerXL
- **License**: MIT (encoder/decoder)
- **Citation**: ISMIR 2021

## Phase 3: Open-Source Transcription and Tablature Tools

### Audio-to-MIDI Transcription

#### 1. Spotify Basic Pitch
- **Repository**: https://github.com/spotify/basic-pitch
- **License**: Apache-2.0
- **Capabilities**: Polyphonic pitch detection, note onset/offset, MIDI output
- **Performance**: Lightweight, real-time capable

#### 2. Omnizart
- **Repository**: https://github.com/Music-and-Culture-Technology-Lab/omnizart
- **License**: MIT
- **Capabilities**:
  - Music (pitched instruments)
  - Drum transcription
  - Vocal melody (note-level and F0)
  - Chord progressions
  - Beat detection
- **Citation**: JOSS 2021

### Guitar Tablature Transcription (Audio → Tab)

#### 1. TabCNN
- **Paper**: "Guitar Tablature Estimation with a Convolutional Neural Network" (ISMIR 2019)
- **Approach**: CNN for string-level fret classification
- **Dataset**: GuitarSet (360 solo acoustic guitar recordings)
- **Limitation**: Solo acoustic guitar only

#### 2. SynthTab
- **Paper**: "Leveraging Synthesized Data for Guitar Tablature Transcription" (ICASSP 2024)
- **Innovation**: Large-scale synthesized guitar tablature dataset from DadaGP
- **Improvement**: Addresses low-resource problem in guitar tablature transcription

#### 3. Guitar Transcription with Inhibition
- **Repository**: https://github.com/cwitkowitz/guitar-transcription-with-inhibition
- **Innovation**: Addresses shortcomings of TabCNN with inhibition objective
- **Dataset**: GuitarSet

### MIDI-to-Tablature Conversion

#### Machine Learning Approach (arXiv:2510.10619)
- **Method**: Deep neural network for probabilistic fretboard prediction
- **Architecture**: CNN with deconvolutional layers for 6×25 fretboard output
- **Features**:
  - Considers 4 previous tablature frames for context
  - Playability constraints (max 6 frets stretch)
  - Handles polyphonic input

### Commercial Tools (Reference)
- **Guitar2Tabs** (Klangio): AI-powered, exports to GuitarPro
- **Songsterr**: AI tab generation from YouTube
- **Tabtify**: Audio to guitar tabs with multiple output formats

