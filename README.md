# Synergetic-Synthesis-Oscillators-for-Korg-NTS-1

Custom oscillator patches for the Korg NTS-1 exploring the non-octaval Synergetic Temperament System and advanced West Coast synthesis.

This repository contains three custom oscillator patches for the Korg NTS-1 mk1. Two patches implement Kenneth Hemmerick's **Synergetic Temperament System**, based on **3D wave formations and closest-packed sphere geometry** rather than traditional octave divisions. The third is an advanced Buchla 259-inspired complex oscillator. Together they offer unique microtonal, inharmonic, and West Coast sonic possibilities. All patches were developed using Pure Data (.pd) and converted via the pd2logue tool.

---

## The Patches

| Patch Name | Source File | Description | Core Ratios |
|:-----------|:------------|:------------|:------------|
| **Synergetic Bell** | `Synergetic_Bell_NTS1_Enhanced.pd` | Core Synergetic Temperament implementation with four "shells" and adjustable ratios. Frequencies derived from nodal points in vector equilibrium structures divided by 12 directions of energy propagation. Features golden ratio (φ ≈ 1.618) FM modulation. | Shells 1-4: **1.0**, **3.5**, **7.666**, **13.5** (adjustable) |
| **Phi Bell** | `PhiBellHeavy.pd` | Optimized variant of Synergetic Bell with fixed ratios for immediate musicality. Reduced FM aggression for cleaner, more melodic bell tones. | Fixed: **1.0**, **3.5**, **7.666**, **13.5** (φ modulation) |
| **Buchla Complex Advanced** | `BuchlaComplex.pd` | Advanced Buchla 259-inspired complex oscillator with through-zero FM, 5-stage cascading wavefolder, symmetry control for asymmetric folding, and order/balance mixing. Features sine carrier, bipolar modulator, full West Coast synthesis. | Variable (Modulator: 0.25-8×, Timbre: 0.1-20, Symmetry: ±100) |

---

## Synergetic Temperament System Theory

Kenneth Hemmerick's system derives frequencies from **vector equilibrium** (cubo-octahedron) structures created by closest-packing spheres around a central sphere. 

**Key Concepts:**
- Frequencies = (outer shell nodal points) ÷ 12 directions of propagation
- First four frequencies: 12÷12=1.0, 42÷12=3.5, 92÷12=7.666, 162÷12=13.5
- System exhibits constant **acceleration rate** of 1.666… cycles/second/second
- **Non-octaval**: Doubling frequency-edge modulation doesn't double nodal points (synergetic behavior)
- Ratios become progressively closer but never reach unity (similar to whole number ratios)

The system continues: 21, 30.166, 41, 53.05, 67.666, 83.5, 101, 120.166...

Full theory documented in `docs/Synergetic_Temperament_System.pdf`

---

## NTS-1 Controls and Parameter Mapping

### Synergetic Bell

| Control | Parameter | Range (Default) | Function |
|:--------|:----------|:----------------|:---------|
| **KNOB A** | `shape` | 0.05-0.8 (0.3) | **Shell Mix** - Amplitude balance across shells 2-4 |
| **KNOB B** | `alt` | 0-600 (150) | **FM Depth** - Modulation intensity in Hz |
| **TYPE +** | `harm2` | 1-8 (3.5) | **Shell 2 Ratio** - Adjustable frequency multiplier |
| **TYPE +** | `harm3` | 1-16 (7.666) | **Shell 3 Ratio** - Explore other synergetic frequencies |
| **TYPE +** | `harm4` | 1-24 (13.5) | **Shell 4 Ratio** - Higher harmonic shells |
| **TYPE +** | `modrat` | 0.5-3 (1.618) | **Modulator Ratio** - FM carrier frequency (φ default) |

**Sound**: Rich, inharmonic bell tones with complex, evolving overtones. The golden ratio modulator creates naturally shifting timbres. Adjust shell ratios to explore the extended synergetic sequence (21, 30.166, 41, etc.).

---

### Phi Bell

| Control | Parameter | Range (Default) | Function |
|:--------|:----------|:----------------|:---------|
| **KNOB A** | `shape` | 0.1-1 (0.5) | **Shell Mix** - Amplitude distribution |
| **KNOB B** | `alt` | 0-1500 (400) | **FM Depth** - Modulation intensity in Hz |

**Fixed Parameters:**
- Shell ratios: 1.0, 3.5, 7.666, 13.5
- Modulator ratio: 1.618 (φ)

**Sound**: Cleaner, more immediately musical bell tones with the synergetic system's inharmonic character but controlled FM for melodic playing. Ideal for harmonic/melodic material.

---

### Buchla Complex Advanced

| Control | Parameter | Range (Default) | Function |
|:--------|:----------|:----------------|:---------|
| **KNOB A** | `shape` | 0.1-20 (2) | **Timbre/Wavefolder Depth** - Harmonic folding intensity |
| **KNOB B** | `alt` | 0-2 (0.5) | **FM Amount** - Through-zero cross-modulation depth |
| **TYPE +** | `modratio` | 0.25-8 (0.5) | **Mod Ratio** - Modulator frequency multiplier |
| **TYPE +** | `symmetry` | -100 to 100 (0) | **Symmetry** - DC offset for asymmetric folding |
| **TYPE +** | `balance` | 0-1 (0.5) | **Balance** - Principal/Modulator mix |
| **TYPE +** | `order` | 0-1 (0.5) | **Order** - Folded/Raw crossfade |

**Timbre Guide:**
- 0.1-1: Clean sine
- 1-8: Progressive folding
- 8-20: Extreme harmonics

**Modulator Ratio Guide:**
- 0.25: Sub-bass
- 1.0: Unison
- 2-8: High harmonics

**Symmetry Guide:**
- Negative: Even harmonics
- Positive: Odd harmonics

**Architecture:**
- Principal: Pure sine wave carrier
- Modulator: Bipolar ramp with variable ratio
- 5-stage wavefolder: Cascading ×3, ×3, ×2, ×2, ×1.5 amplification + clipping
- Through-zero FM: Modulator can push carrier frequency negative
- Full West Coast synthesis within 32KB/6-parameter constraints

**Sound**: Classic Buchla 259 character - woody plucks, metallic bells, aggressive leads, deep sub-bass. Authentic West Coast synthesis textures.

**Preset Suggestions:**
- **Woody Plucks**: shape=5, symmetry=20, alt=0.3, order=0.8
- **Bell Tones**: shape=10, modratio=1.618, balance=0.3
- **Aggressive Leads**: shape=15, alt=1.5, symmetry=-30
- **Sub Bass**: modratio=0.25, shape=2, balance=0.7
- **Metallic Textures**: shape=18, symmetry=50, modratio=2, alt=1.2

---

## Installation

### Via NTS-1 Manager (Recommended)

1. Download `.ntkdigunit` files from the `builds/` directory
2. Install [Korg NTS-1 Librarian](https://www.korg.com/us/support/download/software/0/811/4881/)
3. Connect NTS-1 via USB
4. Launch NTS-1 Librarian
5. Drag `.ntkdigunit` files to user oscillator slots
6. Sync to device

### Manual Installation

1. Download `.ntkdigunit` files from `builds/`
2. Connect NTS-1 via USB (appears as USB drive)
3. Copy files to the oscillator folder
4. Safely eject
5. Power cycle NTS-1
6. Select oscillator via TYPE button

---

## Building from Source

### Requirements

- [Pure Data](https://puredata.info/) (Vanilla)
- [pd2logue Web Converter](https://app.boochow.com/pd2logue/) (no installation needed)

### Steps

1. Open `.pd` patch files from `patches/` in Pure Data
2. Make desired modifications
3. Go to [pd2logue converter](https://app.boochow.com/pd2logue/)
4. Upload modified `.pd` file
5. Select "NTS-1" as target platform
6. Click "Convert"
7. Download generated `.ntkdigunit` file
8. Check memory usage in converter output (keep under 24KB for safety)

### Development Tips

- **Memory limit**: 32KB total (code + variables), aim for <24KB
- **Max parameters**: 6 per oscillator
- **Oscillator count**: Keep under 7 for memory efficiency
- **Parameter smoothing**: Use `pack f 50` + `line~` to avoid zipper noise
- **Integer scaling**: Use integer ranges (e.g., -100 to 100) then multiply by 0.01 internally
- **Avoid**: Browser storage APIs, complex filters, large wavetables

---

## Technical Details

### NTS-1 mk1 Specifications

- **Platform**: Korg logue SDK
- **CPU**: ARM Cortex-M7
- **Sample Rate**: 48kHz
- **Memory**: 32KB for user oscillator (code + variables)
- **Parameters**: Maximum 6 per oscillator
- **File Format**: `.ntkdigunit` (NTS-1 mk1), `.mnlgxdunit` (minilogue xd)

### Patch Complexity

| Patch | Oscillators | Parameters | Est. Memory |
|:------|:------------|:-----------|:------------|
| Synergetic Bell | 5 (osc~) | 6 | ~24KB |
| Phi Bell | 5 (osc~) | 2 | ~18KB |
| Buchla Complex | 3 (phasor~, cos~) | 6 | ~24KB |

### Signal Flow Examples

**Synergetic Bell:**
```
pitch → [modulator × φ] → FM
                ↓
[shell 1] + [shell 2 × 3.5] + [shell 3 × 7.666] + [shell 4 × 13.5]
     ↓           ↓                   ↓                    ↓
  (+ FM)      (+ FM)              (+ FM)               (+ FM)
     ↓           ↓                   ↓                    ↓
  [osc~]      [osc~]              [osc~]               [osc~]
     └───────────┴───────────────────┴────────────────────┘
                            ↓
                      [sum + clip] → output
```

**Buchla Complex:**
```
pitch → [principal phasor~] → cos~ → [5-stage folder] ─┐
   ↓                                                     ├→ [order mix] ─┐
   └→ [mod × ratio] → phasor~ → bipolar → [shape] ─────┘                ├→ output
                          ↓                                              │
                    [× FM depth] → [+ pitch] → phasor~ → cos~ ──────────┘
                                                              [× balance]
```

---

## Theory References

### Synergetic Temperament System

- **Kenneth Hemmerick**: "The Synergetic Temperament System" (1982)
- **R. Buckminster Fuller**: "Synergetics: Explorations in the Geometry of Thinking" (1975)
- Concepts: Vector equilibrium, closest-packed spheres, synergetic geometry
- Formula: `T = (2 + 10F²) ÷ 12` where F = frequency-edge modulation

### Buchla Complex Oscillator

- **Don Buchla**: 259 Complex Waveform Generator (1973)
- **Buchla 259t**: Modern variant with Timbre/Order/Symmetry controls
- Techniques: Through-zero FM, parallel wavefolder stages, asymmetric folding
- West Coast synthesis philosophy: Additive/generative vs. subtractive

### Additional Reading

- [Buchla 259 User Guide](https://modularsynthesis.com/roman/buchla259/) (1981)
- [Vector Equilibrium](https://en.wikipedia.org/wiki/Cuboctahedron) (geometry)
- [Closest Sphere Packing](https://en.wikipedia.org/wiki/Close-packing_of_equal_spheres)

---

## Contributing

Contributions welcome! When submitting patches:

1. **Include both source and compiled files**:
   - `.pd` source in `patches/`
   - `.ntkdigunit` build in `builds/`

2. **Document thoroughly**:
   - Parameter ranges and defaults
   - Sound character description
   - Intended use cases
   - Preset suggestions

3. **Verify specifications**:
   - Memory usage <24KB (check converter output)
   - Max 6 parameters
   - Test on actual hardware

4. **Code quality**:
   - Clean signal routing
   - Parameter smoothing implemented
   - No deprecated objects

### Future Directions

- Karplus-Strong physical modeling
- Additional synergetic frequencies (shell 5: 21, shell 6: 30.166)
- Granular synthesis techniques
- Additive harmonic series
- Alternative modulator ratios (√2, √3, √5)

---

## License

MIT License

Copyright (c) 2024

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

---

## Acknowledgments

- **Kenneth Hemmerick** - Synergetic Temperament System theory and documentation
- **Don Buchla** - Complex oscillator design and West Coast synthesis philosophy
- **R. Buckminster Fuller** - Synergetic Geometry, vector equilibrium concepts
- **Korg** - logue SDK platform and NTS-1 hardware
- **boochow** - pd2logue Pure Data to logue SDK converter
- **Pure Data community** - Miller Puckette and contributors

---

## Links & Resources

- **[pd2logue Converter](https://app.boochow.com/pd2logue/)** - Convert Pure Data patches to NTS-1 oscillators
- **[Korg logue SDK](https://github.com/korginc/logue-sdk)** - Official SDK documentation
- **[NTS-1 User Manual](https://www.korg.com/us/support/download/manual/0/811/4667/)** - Hardware reference
- **[Pure Data](https://puredata.info/)** - Visual programming language for audio
- **[Synergetic Geometry](https://www.rwgrayprojects.com/synergetics/synergetics.html)** - Fuller's concepts online
- **[Buchla & Associates](https://buchla.com/)** - Historic synthesizer designs

---

## Contact & Support

For questions, bug reports, or patch requests:
- Open an issue on GitHub
- Discuss in relevant NTS-1 communities

**NTS-1 Community:**
- [Korg Forums](https://www.korgforums.com/forum/korg-gear/korg-nts-1)
- [Reddit r/synthesizers](https://www.reddit.com/r/synthesizers/)
- [Lines Community](https://llllllll.co/)

---

*Last updated: 2024*

