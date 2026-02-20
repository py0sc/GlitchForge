# datadecay

A browser-native glitch engine for images and GIFs.  
Upload a file, apply procedural corruption, and export an animated result.

**Live Demo:** [https://py0sc.github.io/datadecay/](https://py0sc.github.io/datadecay/)

---

## Overview

`datadecay` runs entirely in the browser using:

- **Pyodide** (CPython compiled to WebAssembly)  
- **NumPy** for array operations  
- **Pillow** for image decoding and encoding  

All processing happens locally. No backend. No uploads. No tracking.

The aesthetic focus: signal degradation, VHS artifacts, pixel sorting, chromatic displacement, and algorithmic corruption.

---

## Features

### Input Formats
- JPG  
- PNG  
- WEBP  
- GIF (multi-frame supported)  

When a GIF is uploaded:
- Frame count is detected via Pillow  
- Each frame is processed individually  
- Output remains animated  

### Effects

Toggle individual transformations:

- RGB Split  
- Pixel Sort  
- Heatmap  
- Invert  
- Color Tint  
- Scan Lines  
- Block Shift  
- Chromatic Aberration  

Effects can be stacked in any combination.

### Parameters

| Control | Description |
|---------|-------------|
| Output Frames | Number of frames generated (3–16) |
| Frame Speed | Delay between frames (20–200ms) |
| Glitch Intensity | Magnitude of distortions |
| Cluster Count | Segmentation / color grouping granularity |
| Sort Strength | Pixel sorting aggressiveness |

Includes a **Randomize All** control for rapid experimentation.

---

## How It Works

1. File is read as Base64 in the browser  
2. Image data is passed into Pyodide  
3. Pillow decodes frames  
4. NumPy applies pixel-level transformations  
5. Frames are recombined into an animated GIF  
6. Result is rendered and available for download  

The entire pipeline executes inside WebAssembly Python.

---

## Why Pyodide?

- Reuse Python’s image ecosystem  
- Leverage NumPy vectorization  
- Keep transformations expressive and deterministic  
- Run everything client-side  

The initial load downloads the Pyodide runtime (~15MB). Subsequent visits are cached.

MIT License
