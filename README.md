# FFT Noise Filtering & Signal Reconstruction

This repository implements a Digital Signal Processing (DSP) pipeline in Python to denoise complex signals. It demonstrates the power of the Fast Fourier Transform (FFT) in isolating dominant frequencies from background noise and reconstructing a clean signal using the Inverse Fast Fourier Transform (IFFT).

## Project Overview

The script performs the following steps:
1. **Signal Generation:** Creates a synthetic signal composed of 4 random sine waves (1Hz–20Hz) combined with Gaussian white noise.
2. **Frequency Analysis:** Uses `numpy.fft.fft` to transform the time-domain signal into the frequency domain.
3. **Filtering:** Applies a magnitude threshold filter (removing components with amplitude < 0.5) to eliminate noise while preserving the core signal frequencies.
4. **Reconstruction:** Uses `numpy.fft.ifft` to convert the filtered frequency data back into a clean time-domain signal.
5. **Visualization:** Plots the original noisy signal, the frequency spectrum, the reconstructed clean signal, and an overlapping comparison.

## Requirements

To run this simulation, you need Python installed with the following libraries:

- `numpy`
- `matplotlib`
- `ipython` (optional, for notebook display features)

## Implementation Details

### Signal Synthesis
The input signal $x(t)$ is generated as a sum of four sine waves with random integer frequencies $f_1, f_2, f_3, f_4$ plus random noise $N(t)$:

$$x(t) = \sum_{i=1}^{4} A_i \sin(2\pi f_i t) + N(t)$$

### The FFT & Filtering Process
1. **FFT:** The time-domain signal is converted to a spectrum of complex numbers representing magnitude and phase.
2. **Thresholding:** We calculate the magnitude of each frequency component. Any frequency bin with a magnitude less than the noise floor (set to 0.5) is zeroed out.
3. **IFFT:** The modified spectrum is transformed back to the time domain, resulting in a smooth signal that retains only the original sine wave components.

## Usage

1. Clone or download the repository.
2. Run the script as a standard Python file or inside a Jupyter Notebook.
3. The script will automatically generate random frequencies for every run, so each execution provides a unique test case.

## Results

The output is a 4-panel visualization:
1. **Noisy Input:** The raw signal with visible jitter.
2. **Frequency Domain:** A stem plot showing the detected peaks (the 4 original frequencies) vs. the low-level noise floor.
3. **Filtered Output:** The clean, reconstructed wave.
4. **Overlap Comparison:** A direct overlay showing how effectively the noise was removed without altering the signal's phase or amplitude.
