---
title: Phase and the Hilbert Transform
description: ''
date: '2022-01-14T10:26:28.490Z'
name: phase-and-the-hilbert-transform
oxa: oxa:RkW3EUemHJbWfgejvqYu/iPPzWDPvyJXSUaUvE4TT
tags:
  - seismic
  - interpretation
  - phase-analysis
---

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/22c85AAuvCsfggYbOLl8.1"}

Phase is a useful underlying property of the analytic trace model of seismic data that can be used as both an interpretation aid and a means to calibrate and check interpretations on a given seismic dataset. We introduce the analytical trace model and demonstrate some of its usages. We provide working code in python for computation of the Hilbert Transform using a robust FFT-based method and explore 2 use cases for such computed quantities. Jupyter notebooks used for computation and generation of the figures are included in this project.

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/vnKn8QYyfYs6TkTfLst7.4"}

# Introduction

The concept of phase permeates seismic data processing and signal processing in general, but it can be awkward to understand, and manipulating it directly can lead to surprising results. It doesn't help that the word phase is used to mean a variety of things, depending on whether we refer to the propagating wavelet, the observed wavelet, post-stack seismic attributes, or an entire seismic data set. Several publications have discussed the concepts and ambiguities {cite:p}`Chant1992Time; Roden1999significance; Liner2002Phase`.

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/ihBcaiMuiszbc8xSI8bd.18"}

```{mdast} phase-and-the-hilbert-transform.mdast.json#GxHu8oyIsl
```

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/Yfh6SnLT7mnAc360vqoz.3"}

The data we are using are the Penobscot 3D {cite:p}`Purves2014Phase` survey from the [Open Seismic Repository](https://opendtect.org/osr/), which is openly licensed CC-BY-SA by the Canada Nova Scotia Offshore Petroleum Board, and dGB Earth Sciences.

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/tZu1sq7uSdChNLqpuWwC.1"}

In this tutorial, we will focus on aspects of phase relevant to the interpreter. We will look at how to manipulate the phase of a seismic trace by manipulating the phase of its Fourier transform and will use that idea to generate the well-known instantaneous phase post-stack attribute. We will also check how close to zero phase our test data set is.

The plots included in this tutorial were created using standard python libraries and the code to reproduce them is available here on Curvenote and on [the SEG tutorials GitHub repo](https://github.com/seg/tutorials-2014/tree/master/1410_Phase).

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/H2BTeuFveCS3EmlFHdmG.2"}

## The Hilbert Transform

The Fourier transform is complex. Taking the transform of any real signal will result in a set of complex coefficients. Complex numbers are essentially 2D vectors, meaning they have two components: magnitude and phase angle. Most of the time when dealing with Fourier transforms, we concentrate on the magnitude, which tells us about the distribution of signal energy through frequency. However, every signal also has a phase spectrum, and the phase encodes the signal's structure ---  the distribution of the signal energy through time. We do not often examine phase spectrum because it is difficult to interpret, but we can manipulate the Fourier phase to change the structure of our signal without affecting its amplitude spectrum.

The Hilbert transform is a linear operator that produces a 90˚ phase shift in a signal, and it is a good first step in our exploration of phase. It is also commonly used in post-stack seismic analysis to generate the analytic signal from which we can compute the standard complex trace attributes such as envelope, instantaneous phase, and instantaneous frequency

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/Rd7b6r0s6W6ufRyGapCa.1"}

The definition of the Hilbert transform is rather cryptic; it is much easier to consider in terms of its Fourier transform definition. The Hilbert transform $H$ of a signal $u$ is related to the Fourier transform $F$ like this:

```{math}
:label: O1i3MDW20K

  F(H(u))(\omega) = \sigma_H(\omega) \cdot F(u)(\omega)
```

where:

```{math}
:label: mLKHopqtdQ

\sigma_{\mathrm{H}}(\omega)=\left\{\begin{array}{l}i \text { for } \omega<0 \\ 0 \text { for } \omega=0 \\ -i \text { for } \omega>0\end{array}\right.
```

So we apply a Hilbert transform by multiplying all negative frequencies by $i$and all positive frequencies by $-i$, leaving any DC component untouched. This is perhaps not intuitive, but we can gain some additional insight by thinking about it geometrically.

The multiplication of two complex numbers $a$ (such as a Fourier coefficient) and $b$ (such as $\sigma_H$ above) can be thought of as a rotation in the complex plane. Euler's formula helps us to see that to rotate any complex number by a specific angle a, we must multiply it by the complex number $\mathrm{e}^{i \alpha}=\cos \alpha+i \sin \alpha$.

We see that multiplication by $i$ alone, as in the equation above, is equivalent to a rotation by 90°. When we take the inverse Fourier transform, the result is a phase-shifted version of our signal.

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/giMLopVlG5ZZBxxiZSwS.1"}

So, we can generalize the definition of the Hilbert above to produce a phase shift to any angle, $\alpha$\:

$$  \sigma_{n}(\omega)=\left\{\begin{array}{l}\mathrm{e}^{i \alpha} \text { for } \omega<0 \\ 0 \text { for } \omega=0 \\ \mathrm{e}^{-i \alpha} \text { for } \omega>0\end{array}\right.$$

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/b9LHNoAEcfl8jSgt8rLk.1"}

## Phase shifting in Python

Let us use this principle to phase-shift a seismic trace using open source python.

````{margin}
NOTE: If you are working in GNU Octave check back to [fftshifter.m on github](https://github.com/seg/tutorials-2014/blob/master/1410_Phase/fftshifter.m).

````

We will take the fast Fourier transform (FFT) of our signal, manipulate the coefficients, and apply the inverse FFT.

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/XnLLyLcMoHu80MrZt5bA.1"}

```python
from math import ceil,exp
from scipy.fftpack import fft, ifft

def fftshifter(x, phase_shift_in_radians):
    # Create an array to apply the coefficient to 
    # positive and negative frequencies appropriately
    N = len(x);
    R0 = np.exp(-1j*phase_shift_in_radians);
    R = np.ones(x.shape, dtype=np.complex);
    R[0]=0.; 
    R[1:N//2] = R0;
    R[N//2:] = np.conj(R0);

    # Apply the phase shift in the frequency domain
    Xshifted = R*fft(x);
    
    # Recover the shifted time domain signal
    y = np.real(ifft(Xshifted));
    
    return y
```

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/9VitJKuZefPzQR0GEgdn.1"}

## Complex Trace Attributes

Now that we have this ability to phase-shift, what can we do with it?

We can now compute some seismic attributes. A whole set of commonly used attributes depends on the Hilbert transform and the code below generates the Hilbert transform, envelope, and phase traces for a trace from the Penobscot data set.

````{important}
If you look closely here you'll see we're actually using the `hilbert` function from `scipy.signal` instead of our arbitrary phase shifter. Whilst the two should be equivalent for 90 degree shifts, I've noted that the `scipy` version is slightly different and produces smoother envelope responses, which I believe are more correct. I think this is down to a windowing step on computation of the FFT that we are omitting in `fftshifter`, but I'll need to check the `scipy` implementation to confirm. Stay tuned for updates on that over in the notebook [phase_and_hilbert_transform.ipynb](oxa:RkW3EUemHJbWfgejvqYu/mNnJgVOim6kyzo1p5ipL "phase_and_hilbert_transform.ipynb") .

````

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/BgZ7fMXq3owK9nPSvdE1.1"}

```python
from scipy.signal import hilbert as hilbert_transform
hilbert = np.zeros_like(seismic)

for x in range(line.shape[0]):
    hilbert[x,:] = np.imag(hilbert_transform(line[x,:])[500:750])

z = seismic + 1j*hilbert
env = np.abs(z)
phase = np.angle(z)
```

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/vbc9u2UdhR4cMAtka5Gd.1"}

See the accompanying notebook for full plotting code. A section of this trace is shown in Figure 2 below.

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/VcYeNrFMSYtf8Nu8DrSv.1"}

```{mdast} phase-and-the-hilbert-transform.mdast.json#USQTSmhusq
```

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/K8iy5N9He8cmGsZOBLm6.1"}

{numref}`Figure %s <pH5UdjSONn>` shows the same attributes now computed over the whole section. These are useful interpretation aids. Once you have the complex trace representation, z, there are many additional attributes that you can compute, such as instantaneous frequency, phase acceleration, and envelope-weighted frequency, the list goes on\\dots merely by playing around with the complex trace.

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/1UA1dMMyGLBD6TXFEQQP.1"}

```{mdast} phase-and-the-hilbert-transform.mdast.json#tU6SUcixAz
```

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/KTOcB686QEuuBqlVZZyK.1"}

## Checking the phase of your seismic

The complex attributes generated from a seismic trace and its Hilbert transform are useful in seismic interpretation. However, the quality of our seismic interpretation depends on another aspect of phase, that is, the phase of our seismic data set and whether the observed wavelet has been corrected to a zero-phase response during processing. {cite:t}`Roden1999significance` give a practical way to assess the phase of seismic data as a quality check for seismic interpretation. They point out that where we have a strong reflection from a sharp geologic interface that we can confidently expect to produce a zero-phase response, we can measure the actual response in the seismic data set on that horizon to determine the amount of phase error present.

The principle that {cite:t}`Roden1999significance` apply is that at strong reflections in zero phase data, we would expect peaks (or troughs) in the trace to align with peaks in the envelope. Therefore, any horizon that we pick on zero-phase data could also be picked on the envelope of that data.

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/tIrSeE4eYvSa9LqwFLrq.1"}

```{mdast} phase-and-the-hilbert-transform.mdast.json#PtUIJJZ8SQ
```

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/6awl5bcQccewlnHCJqnZ.1"}

{numref}`Figure %s <HHx7uissTU>` shows a segment of our trace from {numref}`Figure %s <rZM72vJAR8>` with envelope peaks marked as spikes (see find\\\_peaks.m). In Figure 2b, I have isolated those events and plotted the actual signal phase against the phase we would expect for a zero-phase data set.

The difference between the two could be systematic residual phase. If we think a particular reflector has minimal interference and no AVO or other effects, then the rest is residual phase. The strong trough at the Abenaki reflector in Figure suggests that there could be 0.64 radians, or about 37°, of residual phase in the data. That is something that we could now correct for by phase-shifting all our traces.

We can also look at this phase error at envelope peaks across our dataset as shown in Figure 5 below.

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/nntW22fEZdfrz19UE7Ma.1"}

```{mdast} phase-and-the-hilbert-transform.mdast.json#aNuo8HonAJ
```

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/OQu6iWbNaLDqkop1fiiq.1"}

The Hilbert transform opens up a world of seismic attributes, some of which have everyday application for the interpreter. To run or build on the code clone the repo at <http://github.com/seg/tutorials-2014>.

+++ {"oxa":"oxa:RkW3EUemHJbWfgejvqYu/mZAW3TC7HjpILSwnP4dt.4"}

The official version of this tutorial was published in the SEG's Leading Edge Magazine in October 2014.

```{figure} images/RkW3EUemHJbWfgejvqYu-O6zbn8zq98uZhkHo49a7-v1.jpg
:name: ffA6Fph1zW
:align: center
:width: 30%
```

````{important}
The tutorial is Open Access and licensed under [Creative Commons Share-Alike 4.0 (CC-BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/).

The official tutorial can be found here: <https://doi.org/10.1190/tle33101164.1>

The SEG GitHub repo for the tutorials is here: <https://github.com/seg/tutorials-2014>

This article is a refresh of the original that uses python in place of GNU Octave. It includes all of the figures from the original pre-publication draft. This article is also licensed under [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

The full code is available in [phase_and_hilbert_transform.ipynb](oxa:RkW3EUemHJbWfgejvqYu/mNnJgVOim6kyzo1p5ipL "phase_and_hilbert_transform.ipynb").

All data is available in the [SEG tutorials GitHub repo](https://github.com/seg/tutorials-2014/tree/master/1410_Phase).

All contributions for this article were made by Steve Purves.

````

