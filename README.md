NTS-1 Synergetic & Complex Synthesis
Advanced user oscillators for the Korg NTS-1 mk1, exploring non-octaval temperament systems and West Coast synthesis techniques within the logue SDK constraints.
Patches
Synergetic Bell
Implementation of Kenneth Hemmerick's Synergetic Temperament System - a tuning system based on 3D wave formations and closest-packed sphere geometry rather than octave divisions.
Theory: The system uses frequency ratios (1.0, 3.5, 7.666, 13.5) derived from nodal points in vector equilibrium structures. These frequencies emerge from dividing the number of points in outer shells of closest-packed spheres by 12 (the directions of energy propagation in 3D space). The system produces genuinely non-octaval progressions with a constant second-order difference acceleration of 1.666… cycles/second/second.
Parameters:

KNOB A (shape): Shell mix balance (0.05-0.8)
KNOB B (alt): FM modulation depth (0-600Hz)
harm2: Shell 2 frequency ratio (1-8, default 3.5)
harm3: Shell 3 frequency ratio (1-16, default 7.666)
harm4: Shell 4 frequency ratio (1-24, default 13.5)
modrat: FM modulator ratio (0.5-3, default 1.618/φ)

Sound: Rich, inharmonic bell tones with complex overtone structures. The golden ratio (φ) modulator creates naturally evolving timbres. Adjusting shell ratios lets you explore other frequencies from the synergetic system (21, 30.166, 41, etc.).

Buchla Complex Oscillator
Advanced implementation of the Buchla 259 complex oscillator with through-zero FM, 5-stage wavefolder, and symmetry control.
Architecture:

Principal oscillator: Pure sine wave carrier
Modulator oscillator: Bipolar ramp with variable ratio
5-stage cascading wavefolder (×3, ×3, ×2, ×2, ×1.5)
Through-zero frequency modulation
Asymmetric folding via DC offset (symmetry)
Crossfade mixing (order, balance)

Parameters:

KNOB A (shape): Timbre/wavefolder depth (0.1-20)

0.1-1: Clean sine
1-8: Progressive harmonic folding
8-20: Extreme West Coast textures


KNOB B (alt): FM amount/depth (0-2)
modratio: Modulator frequency ratio (0.25-8, default 0.5)
symmetry: DC offset for asymmetric folding (-100 to 100)
balance: Principal/modulator mix (0-1)
order: Folded/raw signal crossfade (0-1)

Sound: Classic West Coast synthesis - woody plucks, metallic bells, aggressive leads, deep sub-bass. The combination of wavefolder harmonics and through-zero FM creates the distinctive Buchla character.
Presets to try:

Woody plucks: shape=5, symmetry=20, alt=0.3, order=0.8
Bell tones: shape=10, modratio=1.618, balance=0.3
Aggressive leads: shape=15, alt=1.5, symmetry=-30
Sub bass: modratio=0.25, shape=2, balance=0.7


Phi Bell (Heavy)
Optimized variant of the Synergetic Bell with reduced FM aggression and fixed harmonic ratios for more immediately musical tones.
Parameters:

KNOB A (shape): Shell mix (0.1-1)
KNOB B (alt): FM depth (0-1500Hz)
Fixed ratios: 1.0, 3.5, 7.666, 13.5
Fixed modulator: 1.618 (φ)

Sound: Smooth, bell-like tones with the synergetic system's inharmonic character but more controlled FM for melodic playing.

Technical Details
NTS-1 mk1 Constraints:

32KB memory limit for oscillator code + variables
Maximum 6 parameters per oscillator
No browser storage APIs (localStorage/sessionStorage)
Integer or low-resolution parameter values

Development:

Built using Pure Data patches
Converted via pd2logue
Generates .ntkdigunit files for NTS-1 mk1
Signal rate: 48kHz

Design Principles:

Minimal object count (5-7 oscillators max)
Efficient signal routing
Parameter smoothing via pack f 50 + line~
Integer parameter ranges scaled internally (e.g., symmetry: -100 to 100 → ×0.01)


Installation

Download the .ntkdigunit file from builds/
Connect NTS-1 to computer via USB
Mount as USB drive
Copy .ntkdigunit to the oscillator folder
Safely eject and power cycle the NTS-1
Select the oscillator via TYPE button


Theory References
Synergetic Temperament System:

Kenneth Hemmerick's original paper (included in docs/)
Based on R. Buckminster Fuller's Synergetic Geometry
Vector equilibrium and closest-packed sphere structures
Non-octaval frequency progression

Buchla Complex Oscillator:

Don Buchla's original 259 Complex Waveform Generator (1973)
Through-zero FM synthesis
Parallel wavefolder architecture
Symmetry control for even/odd harmonic emphasis


Building from Source

Install Pure Data
Open .pd patches from patches/
Upload to pd2logue converter
Select "NTS-1 mk1" output format
Download generated .ntkdigunit file

Modification tips:

Keep oscillator count under 7 for memory safety
Use pack f 50 + line~ for parameter smoothing
Scale small float ranges to integers (multiply input, divide internally)
Test memory usage in converter output


Contributing
Issues and pull requests welcome. When submitting patches:

Include both .pd source and compiled .ntkdigunit
Document parameter ranges and intended sound character
Verify memory usage is under 24KB for headroom


License
MIT License - see LICENSE file

Acknowledgments

Kenneth Hemmerick - Synergetic Temperament System theory
Don Buchla - Complex oscillator design
R. Buckminster Fuller - Synergetic Geometry
Korg - logue SDK and NTS-1 platform
boochow - pd2logue converter


Links

pd2logue Converter
Korg logue SDK
NTS-1 User Manual
