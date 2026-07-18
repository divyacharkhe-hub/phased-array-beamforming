# Phased array beamforming console

An interactive, radar-console-style visualizer for phased array beamforming — the core technique behind 5G massive MIMO base stations, radar, and sonar systems.

**Live demo:** https://phased-array-beamforming.netlify.app/

![screenshot](screenshot.png)

## What it does

Beamforming uses multiple antennas, each fed with a precisely calculated phase shift, so their signals combine constructively in one direction and cancel out in others — effectively "pointing" a beam without moving anything physically.

This console lets you:

- Adjust the **number of antenna elements** (2–16)
- Adjust **element spacing** in wavelengths (d/λ)
- **Steer the beam** by dragging directly on the polar radiation pattern, or via the slider
- Watch a **live animated wavefield** showing actual wave propagation and interference from each element
- See **grating lobe warnings** — a real antenna design failure mode where spacing too wide creates unwanted duplicate beams

## The math

For an N-element linear array with spacing `d` (in wavelengths) steered to angle `θ0`, the array factor is:

**AF(θ) = (1/N) · |Σ exp(j · 2π · d · n · (sin θ − sin θ0))|**  for n = 0 to N−1

Plotted in dB, this gives the radiation pattern shown in the polar plot.

**Grating lobes** appear when spacing is too large relative to wavelength. They occur at angles where:

**sin(θ0) + m/d = sin(θ_grating)**, for integer m ≠ 0, where |sin(θ0) + m/d| ≤ 1

Try `d/λ = 1.0` and steer to 30° — a full-strength grating lobe appears at −30°, which is exactly why real systems keep element spacing near 0.5λ.

## Tech

Single self-contained HTML file — vanilla JavaScript, HTML5 canvas, no dependencies or build step.

## Background

Built as a companion visualization to an OFDM/MIMO communication system simulation, extending the same antenna-array math into the spatial/beamforming domain used in 5G NR massive MIMO.
