# Hothouse Effect Template

Template for building guitar pedal effects on the [Hothouse DIY DSP Platform](https://www.clevelandmusicco.com/) using the Daisy Seed.

## Getting Started

1. Click **"Use this template"** on GitHub to create a new repo for your effect
2. Install the [Daisy toolchain](https://daisy.audio/tutorials/cpp-dev-env/)
3. Clone your new repo:
   ```bash
   git clone <your-repo-url>
   ```
4. Initialize, update, and build the submodule libraries:
   ```bash
   make submodules
   ```
5. Enable the pre-commit formatting hook:
   ```bash
   git config core.hooksPath .githooks
   ```
6. Set `TARGET` in the `Makefile` to your effect name
7. Write your DSP code in `main.cpp`

## Building & Flashing

```bash
make submodules   # Initialize/update and build submodule libraries
make              # Build firmware
make clean        # Clean build artifacts
make program-dfu  # Flash via USB DFU
```

To enter DFU mode, long-press footswitch 1 (2 seconds) or hold BOOT + press RESET on the Daisy Seed.

## Hardware Controls

| Control | Access |
|---|---|
| Knobs 1–6 | `hw.GetKnobValue(Hothouse::KNOB_1)` — returns `0.0–1.0` |
| Toggle switches 1–3 | `hw.GetToggleswitchPosition(Hothouse::TOGGLESWITCH_1)` — returns UP/MIDDLE/DOWN |
| Footswitch 1 | Available for effect control |
| Footswitch 2 | Bypass toggle (pre-wired in template) |
| LED 1 | Available for effect status |
| LED 2 | Bypass indicator (pre-wired in template) |

## Libraries

- [libDaisy](https://github.com/electro-smith/libDaisy) — Hardware abstraction
- [DaisySP](https://github.com/electro-smith/DaisySP) — DSP modules (reverbs, delays, filters, oscillators, etc.)
