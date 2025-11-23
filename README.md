# Synergetic-Synthesis-Oscillators-for-Korg-NTS-1
Custom oscillator patches for the Korg NTS-1 exploring the non-octaval Synergetic Temperament System.

This repository contains a set of three custom oscillator patches for the Korg NTS-1, all inspired by and implementing aspects of Synergetic Temperament System. This system is based on **3D wave formations and closest-packed sphere geometry** rather than traditional octave divisions, offering a unique microtonal and inharmonic sonic palette. The patches were developed using the pd2logue converter from Pure Data (.pd) files.

### The Patches

| Patch Name | Source File | Description | Core Ratios |
| :--- | :--- | :--- | :--- |
| **Synergetic Bell** | | The core Synergetic temperament implementation, designed to use four "shells". The frequencies are derived from nodal points in vector equilibrium structures. | Shells 1-4 Ratios: **1.0**, **3.5**, **7.666**, **13.5** |
| **Phi Bell** | | An optimized variant of the Synergetic Bell for cleaner, less aggressive bell tones. It features FM modulation at the Golden Ratio, $\phi \approx 1.618$. | Same Shell Ratios as Synergetic Bell |
| **Buchla Complex** | | A cross-modulation oscillator with waveshaping, included as a general-purpose bonus oscillator. Note: This patch does not directly implement the Synergetic Temperament ratios. | N/A (Focuses on FM/Waveshaping relationships) |

### NTS-1 Controls and Mapping

The three NTS-1 front-panel knobs are mapped to the following parameters for real-time control:

#### 1. Synergetic Bell & Phi Bell

| NTS-1 Knob | Parameter Name | Range/Default (Synergetic) | Range/Default (Phi) | Function |
| :--- | :--- | :--- | :--- | :--- |
| **A** | `shape` | 0.05 to 0.8 (Default: 0.3) | 0.1 to 1 (Default: 0.5) | **Shell Mix** (Controls the amplitude distribution across the four shells) |
| **B** | `alt` | 0 to 600 (Default: 150) | 0 to 1500 (Default: 400) | **FM Depth** (Depth of the FM Modulator) |
| **C** | `modrat` | 0.5 to 3 (Default: 1.618) | N/A (Fixed 1.618 in Phi Bell) | **Mod Ratio** (Frequency ratio for the FM Modulator) |

#### 2. Buchla Complex

| NTS-1 Knob | Parameter Name | Range/Default | Function |
| :--- | :--- | :--- | :--- |
| **A** | `shape` | 0.1 to 10 (Default: 2) | **Timbre / Waveshape** (Applied to Principal Oscillator) |
| **B** | `alt` | 0 to 1 (Default: 0.3) | **FM Amount** (Cross-modulation depth) |
| **C** | (Not used in core patch) | N/A | (Free for further mapping) |
| **D** | `modratio` | 0.25 to 4 (Default: 0.5) | **Mod Ratio** (Frequency ratio for the Modulator Oscillator) |

***

### Installation

1.  Download the compiled KORG patch files (e.g., `.ntkdigunit`, `.unit`) from the **`builds/`** directory.
2.  Use the KORG minilogue/NTS-1 Librarian/Manager software on your computer.
3.  Connect your NTS-1 via USB.
4.  Drag and drop the files into the designated `user OSC` slot on the NTS-1 Manager.
