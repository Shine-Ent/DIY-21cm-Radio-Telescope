# Project Journal: 21-cm Radio Telescope

Date: Tuesday, April 7th
Status: Starting the project

## Current Status
Started the project after reading ASU paper "Low Cost Radio Telescope for Galactic 21cm Observations" as my main starting point.

Ordered the core electronics from Amazon, and they should arrive by April 15th:
- Nooelec SAWbird+ H1 (LNA and Filter combo)
- RTL-SDR Blog V3 (The receiver)

---

## Research and Physics Notes
Questions and answeres I have achived after research

## Hardware & Electronics (The RF Chain)

**What electronic components should I prioritize buying first?**
The core receiver chain: an RTL-SDR dongle (the digitizer) and a Low-Noise Amplifier/Filter (to boost and isolate the signal). 

**Is it feasible to build my own Low-Noise Amplifier (LNA) for this project?**
It is highly difficult at 1.4 GHz due to parasitic capacitance and strict impedance matching requirements. It is strategically better to use a commercial LNA to prove the telescope works, and design a custom LNA later as a "Phase 2" portfolio piece.

**What type of bandpass filter is required for the 1.42 GHz hydrogen line?**
A highly-tuned, narrow filter centered exactly at 1420 MHz to act as a brick wall against local terrestrial noise (like cell phones and Wi-Fi).

**Does the Nooelec SAWbird+ H1 function as an "all-in-one" replacement?**
Yes. It contains two cascading LNAs and a centered 1420 MHz SAW filter on a single board, which drastically reduces insertion loss compared to stringing separate components together with cables.

**What are the physical hardware connections?**
Copper Probe $\rightarrow$ SMA Panel Mount $\rightarrow$ SMA Cable $\rightarrow$ SAWbird H1 $\rightarrow$ SMA Cable $\rightarrow$ RTL-SDR $\rightarrow$ USB Laptop.

---

## Antenna Physics & Geometry (The Horn)

**Why is the antenna shaped like a pyramid rather than a cone?**
Pyramids are easier to fabricate from rigid foam and naturally feed into a rectangular waveguide, which captures linearly polarized waves using a simple, straight piece of copper wire.

**What is the difference between observing the Sun versus the Galaxy?**
The Sun is extremely "loud" in RF and is used to calibrate and test the baseline function of the telescope. The Milky Way is faint and sprawling, requiring the horn's wide field of view to average out the signals across massive hydrogen clouds.

**Why must the horn antenna be so physically large?**
Antenna size scales with wavelength. The 1.4 GHz hydrogen line has a massive 21.1 cm wavelength, requiring an opening roughly four times that size (~90 cm) to achieve sufficient gain.

**What would change if we made the horn opening larger than 89.7 cm?**
Increasing the aperture increases the Gain (signal strength) but drastically narrows the Beamwidth, requiring motorized tracking mounts to follow the sky, while also making the structure physically unwieldy.

---

## Waveguide Theory & Electromagnetics

**What is a waveguide, and how does it differ from the Poynting vector?**
The Poynting vector is the mathematical arrow showing the direction electromagnetic energy is traveling. A waveguide is the physical metal pipe built to trap that vector and force the energy to travel in one specific direction without spreading.

**What is the difference between a rectangular and a circular waveguide?**
Rectangular waveguides force linear polarization (straight up-and-down waves). Circular waveguides allow circular polarization (spiraling waves), which require complex, difficult-to-build helical antennas to capture.

**Why does the waveguide box need to be strictly rectangular instead of square?**
A strict 2:1 rectangular shape physically suppresses side-to-side waves, forcing 100% of the electromagnetic energy into a perfect, predictable up-and-down vertical orientation.

**What does it mean for a wave to be in the "Transverse Electric 1,0" (TE₁₀) mode?**
It means the wave's electric field is perpendicular to its forward travel, and it forms exactly one energy peak perfectly centered in the middle of the box—which tells us exactly where to place our copper wire probe.

**How does the pyramidal horn act as an "impedance transformer"?**
The gradual flare of the pyramid smoothly transitions the 377-Ohm impedance of empty space to the higher impedance of the waveguide, preventing the wave from violently reflecting away from the metal.

**Why does empty space cause radio waves to reflect off a sudden metal opening?**
Just like light hitting a sudden dense pane of glass, a radio wave hitting an abrupt metal boundary experiences an "impedance mismatch." The physics of this sudden boundary forces the energy to bounce back.

---

## Beamwidth & Phase Interference

**What does "beamwidth" mean in radio astronomy?**
It is the "field of view" of the antenna; the angular cone in the sky where the telescope is most sensitive to incoming signals. 

**Why does increasing the physical size of the antenna decrease the beamwidth?**
A wider antenna surface causes waves arriving at an angle to hit the left and right sides of the aperture at drastically different times. This timing delay causes the electrical signals to cancel each other out (destructive interference).

**Why doesn't a wider antenna simply collect more waves from all directions?**
Radio energy travels as waves, not particles. If a wave hits a wide surface at an angle, the peaks and valleys of the wave electrically cancel each other out before they ever reach the receiver.
