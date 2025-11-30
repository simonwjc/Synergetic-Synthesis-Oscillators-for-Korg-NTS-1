# Synergetic-Synthesis-Oscillators-for-Korg-NTS-1

Custom oscillator patches for the Korg NTS-1 exploring **R. Buckminster Fuller's Synergetic Geometry** applied to synthesis, plus advanced West Coast techniques and classic digital emulation.

This repository contains five custom oscillator patches for the Korg NTS-1 mk1. Three patches implement **R. Buckminster Fuller's Synergetic Geometry** (as applied to temperament by Kenneth Hemmerick), based on **3D wave formations and closest-packed sphere geometry** rather than traditional octave divisions. The fourth is an advanced Buchla 259-inspired complex oscillator, the fifth is an FS1R-inspired formant synthesizer, and the sixth is a Kawai K1R-inspired dual oscillator. Together they offer unique microtonal, inharmonic, West Coast, and classic digital sonic possibilities.

All patches developed using Pure Data (.pd) and converted via [pd2logue](https://app.boochow.com/pd2logue/). Download ready-to-use `.ntkdigunit` files from the releases.

-----

## The Patches

|Patch Name          |File                         |Description                                                                                                                                                                                                                                    |Core Ratios                                    |
|:-------------------|:----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------|
|**Synergetic Bell** |`synergetic_bell.ntkdigunit` |Core implementation of Fuller's Synergetic Geometry with four "shells". Frequencies derived from nodal points in vector equilibrium structures divided by 12 directions of energy propagation. Features golden ratio (φ ≈ 1.618) FM modulation.|Shells: **1.0, 3.5, 7.666, 13.5** (adjustable) |
|**Phi Bell**        |`phi_bell.ntkdigunit`        |Optimized variant with fixed ratios for immediate musicality. Reduced FM aggression for cleaner, melodic bell tones.                                                                                                                           |Fixed: **1.0, 3.5, 7.666, 13.5** (φ modulation)|
|**Buchla Complex**  |`buchla_complex.ntkdigunit`  |Advanced Buchla 259-inspired oscillator with through-zero FM, 5-stage cascading wavefolder, symmetry control, order/balance mixing. Full West Coast synthesis.                                                                                 |Variable (Mod: 0.25-8×, Timbre: 0.1-20)        |
|**Formant Partials**|`formant_partials.ntkdigunit`|FS1R-inspired formant synthesizer with 5 independent partials, vowel formants, and multiple harmonic series. Vocal synthesis capabilities.                                                                                                     |Variable spectra + vowel formants              |
|**K1R Dual**        |`k1r_dual.ntkdigunit`        |Kawai K1R-inspired dual oscillator with variable harmonic ratios and crossfade mixing. Classic late-80s digital PCM synthesis character with cold, glassy tones.                                                                               |Dual sources: **1-4× harmonics** (adjustable)  |

-----

## Fuller's Synergetic Geometry Applied to Music

**R. Buckminster Fuller** developed Synergetic Geometry in the 1970s, describing nature's coordinate system through closest-packed spheres and vector equilibrium structures. **Kenneth Hemmerick** applied this to music in 1982, creating the Synergetic Temperament System.

### Key Concepts:

- **Frequencies = (outer shell nodal points) ÷ 12 directions of propagation**
- First four frequencies: 12÷12=**1.0**, 42÷12=**3.5**, 92÷12=**7.666**, 162÷12=**13.5**
- System exhibits constant **acceleration rate** of **1.666… cps/cps**
- **Non-octaval**: Doubling frequency-edge modulation doesn't double nodal points (synergetic behavior)
- Ratios progressively approach but never reach unity

The system continues: **21, 30.166, 41, 53.05, 67.666, 83.5, 101, 120.166…**

Full theory: `docs/Synergetic_Temperament_System.pdf`

-----

## Controls & Parameters

### Synergetic Bell

|Control   |Parameter|Range (Default)|Function                                           |
|:---------|:--------|:--------------|:--------------------------------------------------|
|**KNOB A**|`shape`  |0.05-0.8 (0.3) |**Shell Mix** - Amplitude balance across shells 2-4|
|**KNOB B**|`alt`    |0-600 (150)    |**FM Depth** - Modulation intensity in Hz          |
|**TYPE +**|`harm2`  |1-8 (3.5)      |**Shell 2 Ratio** - Adjustable frequency multiplier|
|**TYPE +**|`harm3`  |1-16 (7.666)   |**Shell 3 Ratio** - Explore synergetic frequencies |
|**TYPE +**|`harm4`  |1-24 (13.5)    |**Shell 4 Ratio** - Higher harmonic shells         |
|**TYPE +**|`modrat` |0.5-3 (1.618)  |**Modulator Ratio** - FM carrier (φ default)       |

**Sound**: Rich, inharmonic bell tones with complex evolving overtones. Golden ratio modulator creates naturally shifting timbres. Adjust shell ratios to explore extended sequence (21, 30.166, 41…).

-----

### Phi Bell

|Control   |Parameter|Range (Default)|Function                                 |
|:---------|:--------|:--------------|:----------------------------------------|
|**KNOB A**|`shape`  |0.1-1 (0.5)    |**Shell Mix** - Amplitude distribution   |
|**KNOB B**|`alt`    |0-1500 (400)   |**FM Depth** - Modulation intensity in Hz|

**Fixed**: Shell ratios 1.0, 3.5, 7.666, 13.5 | Modulator 1.618 (φ)

**Sound**: Cleaner, more musical bell tones with synergetic inharmonic character but controlled FM. Ideal for melodic material.

-----

### Buchla Complex Advanced

|Control   |Parameter |Range (Default)|Function                                              |
|:---------|:---------|:--------------|:-----------------------------------------------------|
|**KNOB A**|`shape`   |0.1-20 (2)     |**Timbre/Wavefolder** - Harmonic folding intensity    |
|**KNOB B**|`alt`     |0-2 (0.5)      |**FM Amount** - Through-zero cross-modulation         |
|**TYPE +**|`modratio`|0.25-8 (0.5)   |**Mod Ratio** - Modulator frequency (0.25=sub, 8=high)|
|**TYPE +**|`symmetry`|-100 to 100 (0)|**Symmetry** - DC offset (negative=even, positive=odd)|
|**TYPE +**|`balance` |0-1 (0.5)      |**Balance** - Principal/Modulator mix                 |
|**TYPE +**|`order`   |0-1 (0.5)      |**Order** - Folded/Raw crossfade (Buchla 259t style)  |

**Architecture**: Pure sine carrier + bipolar modulator | 5-stage wavefolder (×3, ×3, ×2, ×2, ×1.5) | Through-zero FM

**Sound**: Classic Buchla 259 - woody plucks, metallic bells, aggressive leads, deep sub-bass.

**Presets**:

- Woody Plucks: shape=5, symmetry=20, alt=0.3, order=0.8
- Bell Tones: shape=10, modratio=1.618, balance=0.3
- Aggressive Leads: shape=15, alt=1.5, symmetry=-30
- Sub Bass: modratio=0.25, shape=2, balance=0.7

-----

### Formant Partials (FS1R-Inspired)

|Control   |Parameter |Range (Default)|Function                                                |
|:---------|:---------|:--------------|:-------------------------------------------------------|
|**KNOB A**|`shape`   |0-100 (50)     |**Formant** - Amplitude envelope (0=bass, 100=bright)   |
|**KNOB B**|`alt`     |0-100 (50)     |**Brightness** - Upper partial multiplier (×0.8 to ×8.8)|
|**TYPE +**|`spectrum`|0-4 (0)        |**Spectrum Type** - Harmonic series selection           |
|**TYPE +**|`vowel`   |0-4 (0)        |**Vowel Formant** - Vocal character (A/E/I/O/U)         |
|**TYPE +**|`detune`  |-50 to 50 (0)  |**Detune** - Chorus effect (±5%)                        |

**Spectrum Types**:

- 0: **Harmonic** (1,2,3,4,5) - Natural, warm
- 1: **Odd+Even** (1,2,3,5,7) - Slightly hollow
- 2: **Odd Only** (1,3,5,7,9) - Square wave character
- 3: **Even Heavy** (1,2,4,6,8) - Organ-like
- 4: **Inharmonic** (1,1.5,2.5,3.5,5) - Bell-like, FS1R style

**Vowel Formants**:

- 0: **/A/ "ah"** - Open, bright
- 1: **/E/ "eh"** - Mid, focused
- 2: **/I/ "ee"** - Narrow, nasal
- 3: **/O/ "oh"** - Round, dark
- 4: **/U/ "oo"** - Very round

**Sound**: Clean vocal synthesis, FS1R-style pads, formant-shaped tones. 5 independent sine partials with vowel-like amplitude shaping.

**Presets**:

- Vocal Pad: spectrum=0, vowel=0, formant=50, brightness=40, detune=15
- FS1R Bell: spectrum=4, vowel=2, formant=70, brightness=80
- Warm Organ: spectrum=3, vowel=3, formant=30, brightness=50, detune=5

-----

### K1R Dual (Kawai K1R-Inspired)

|Control   |Parameter |Range (Default)|Function                                              |
|:---------|:---------|:--------------|:-----------------------------------------------------|
|**KNOB A**|`shape`   |0-100 (50)     |**Osc 2 Frequency** - Harmonic multiplier (1-4×)     |
|**KNOB B**|`alt`     |0-100 (50)     |**Mix Balance** - Crossfade between oscillators       |
|**TYPE +**|`spectrum`|0-100 (80)     |**Overall Level** - Master output amplitude           |

**Architecture**: Dual sine oscillators with independent frequency control

**Sound**: Cold, glassy digital timbre reminiscent of late-80s PCM synthesis. Clean harmonic intervals with vintage digital character.

**Presets**:

- Glassy Pad: shape=50, alt=50, spectrum=70
- Digital Bell: shape=75, alt=30, spectrum=80
- Cold Lead: shape=90, alt=60, spectrum=90
- Dual Unison: shape=0, alt=100, spectrum=80
- Metallic Texture: shape=100, alt=40, spectrum=75

-----

## Installation

### Via NTS-1 Manager (Recommended)

1. Download `.ntkdigunit` files from [Releases](../../releases)
1. Install [Korg NTS-1 Librarian](https://www.korg.com/us/support/download/software/0/811/4881/)
1. Connect NTS-1 via USB
1. Launch NTS-1 Librarian
1. Drag files to user oscillator slots
1. Sync to device

### Manual Installation

1. Download `.ntkdigunit` files from [Releases](../../releases)
1. Connect NTS-1 via USB (mounts as drive)
1. Copy to oscillator folder
1. Safely eject & power cycle
1. Select via TYPE button

-----

## Building from Source (Optional)

If you want to modify the patches:

### Requirements

- [Pure Data](https://puredata.info/) (Vanilla)
- [pd2logue converter](https://app.boochow.com/pd2logue/) (web-based)
- Source `.pd` files (available on request)

### Steps

1. Open `.pd` file in Pure Data
1. Make modifications
1. Upload to pd2logue converter
1. Select "NTS-1" target
1. Download `.ntkdigunit` file
1. Check memory usage (<24KB recommended)

### Development Tips

- **Memory**: 32KB limit, aim for <24KB
- **Parameters**: Max 6 per oscillator
- **Smoothing**: Use `pack f 50` + `line~`
- **Integer params**: Scale 0-100 then multiply by 0.01
- **Avoid**: `expr`, browser storage, complex filters

-----

## Technical Specifications

**NTS-1 mk1**:

- Platform: Korg logue SDK
- CPU: ARM Cortex-M7
- Sample Rate: 48kHz
- Memory: 32KB (code + variables)
- File Format: `.ntkdigunit`

**Patch Complexity**:

|Patch           |Oscillators      |Parameters|Memory|
|:---------------|:----------------|:---------|:-----|
|Synergetic Bell |5 (osc~)         |6         |~24KB |
|Phi Bell        |5 (osc~)         |2         |~18KB |
|Buchla Complex  |3 (phasor~, cos~)|6         |~24KB |
|Formant Partials|5 (osc~)         |6         |~22KB |
|K1R Dual        |2 (osc~)         |3         |~18KB |

-----

## Theory & References

### Synergetic Geometry

- **R. Buckminster Fuller**: "Synergetics: Explorations in the Geometry of Thinking" (1975)
- **Kenneth Hemmerick**: "The Synergetic Temperament System" (1982)
- Concepts: Vector equilibrium, closest-packed spheres, synergetic geometry
- Formula: `T = (2 + 10F²) ÷ 12` where F = frequency-edge modulation

### Buchla Complex Oscillator

- **Don Buchla**: 259 Complex Waveform Generator (1973)
- Techniques: Through-zero FM, parallel wavefolder, asymmetric folding
- Philosophy: Additive/generative West Coast synthesis

### FS1R Formant Synthesis

- **Yamaha FS1R**: Formant Sequence Synthesis (1998)
- Independent partial control with vocal formant shaping
- Combines FM with formant filtering concepts

### Kawai K1/K1R Digital Synthesis

- **Kawai K1**: PCM waveform + digital filter hybrid synthesizer (1988)
- **Kawai K1R**: Rack-mount version with expanded multitimbral capability (1989)
- Techniques: Dual PCM source mixing, digital resonant filtering, preset-based workflow
- Philosophy: Affordable digital synthesis with distinctive "cold glass" character
- Notable users: 808 State, The Prodigy, 90s dance/electronic production

### Additional Reading

- [Buchla 259 User Guide](https://modularsynthesis.com/roman/buchla259/) (1981)
- [Vector Equilibrium](https://en.wikipedia.org/wiki/Cuboctahedron)
- [Closest Sphere Packing](https://en.wikipedia.org/wiki/Close-packing_of_equal_spheres)
- [Kawai K1 Service Manual](https://www.synthxl.com/kawai-k1/) (1988)
- [Digital Synthesis History: The Hybrid Era](https://www.vintagesynth.com/kawai/k1.php)
- [K1 vs M1: The Digital Divide](https://www.soundonsound.com/reviews/kawai-k1r)

-----

## Contributing

Contributions welcome! When submitting new oscillators:

- Provide compiled `.ntkdigunit` file
- Include parameter documentation
- Provide sound descriptions & preset suggestions
- Verify: Memory <24KB, max 6 parameters, tested on hardware
- Source `.pd` files optional but appreciated

-----

## License

MIT License - Copyright (c) 2024

See LICENSE file for full text.

-----

## Acknowledgments

- **R. Buckminster Fuller** - Synergetic Geometry, vector equilibrium concepts
- **Kenneth Hemmerick** - Synergetic Temperament System application to music
- **Don Buchla** - Complex oscillator design, West Coast synthesis
- **Yamaha** - FS1R formant synthesis concepts
- **Kawai** - K1/K1R digital synthesis architecture
- **Korg** - logue SDK and NTS-1 platform
- **boochow** - pd2logue converter
- **Pure Data community** - Miller Puckette and contributors

-----

## Links & Resources

- [pd2logue Converter](https://app.boochow.com/pd2logue/)
- [Korg logue SDK](https://github.com/korginc/logue-sdk)
- [NTS-1 User Manual](https://www.korg.com/us/support/download/manual/0/811/4667/)
- [Pure Data](https://puredata.info/)
- [Synergetic Geometry Online](https://www.rwgrayprojects.com/synergetics/synergetics.html)

**Community**:

- [r/synthesizers](https://reddit.com/r/synthesizers)
- [Korg Forums](https://www.korgforums.com/forum/korg-gear/korg-nts-1)
- [Lines Community](https://llllllll.co/)

-----

*Last updated: 2024*
