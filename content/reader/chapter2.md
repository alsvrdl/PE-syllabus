---
title: Chapter 2 - Signal processing
numbering:
  headings: true
  enumerator: 2.%s
---


In physical experiments, we measure signals for a certain amount of time after which the signal is cut off, this is called windowing. Moreover, the measuring of physical phenomena takes place at discrete time intervals through sampling. This is necessary when the measurements have to be digitized before they can be processed by a computer.

However, sampling and windowing will cause artifacts in the information contained within the signal. For instance, sampling causes high-frequency changes between two sample points to not be recorded. Before we explore artifacts further in Section {ref}`sectie:artefacten` we introduce a powerful mathematical tool that will simplify the interpretation of the processes that cause these artifacts, namely convolution.

## Convolution

We have already encountered the convolution operator in Section {ref}`sec:impulsestep`, where we also already saw hints of an important connection between this convolution operator and the Fourier Transform. Here we will formalize that relation.

- **Convolution:** Let $u(x)$ and $v(x)$ be two functions. The convolution of $u(x)$ and $v(x)$, $y(x)$, is defined as:


  $$
  y(x)=\int_{-\infty}^\infty u(s) v(x-s) \mathrm{d}s \overset{\text{def}}{=} u(x) \otimes v(x) 
  $$ (eq:convolution)
  
  The convolution operation is commutative, $u \otimes v = v \otimes u$,distributive,
  $u \otimes (v_1 + v_2)=u \otimes v_1 + u \otimes v_2,$ and associative,
  $u \otimes (v \otimes w)=(u \otimes v)\otimes w.$
- **Convolution theorem:** The Fourier Transform $Y(\omega)$ of the product of two signals $x_1(t)$ and $x_2(t)$ is equal to the convolution of their individual Fourier Transforms:
  
  ```{math}
  :label: eq-convolutie
  \begin{aligned}
  y(t)&=x_1(t)x_2(t),\\
  Y(\omega)&=\frac{1}{2\pi}X_1(\omega)\otimes X_2(\omega).
  \end{aligned}
  ```
  
  Note that the factor $1/2\pi$ depends on the definition (Equation {ref}`eq-FT`) of the Fourier Transform. We have a similar relationship for the reverse case: the convolution of functions in the time domain is given by the Fourier Transform of the product of the Fourier Transforms of the individual functions:
  
- **Proof of the convolution theorem:** Using the Fourier Transform (Equation {ref}`eq-FT`):

```{math}
:label: eq-conv-proof

\begin{aligned}
Y(\omega)
&=\frac{1}{2\pi}X_1(\omega) \otimes X_2(\omega)\\
&=\frac{1}{2\pi}\int_{-\infty}^\infty X_1(s)X_2(\omega-s)\,\mathrm{d}s\\
&=\frac{1}{2\pi}\int_{-\infty}^\infty
\left(\int_{-\infty}^\infty x_1(t)e^{-ist}\,\mathrm{d}t\right)
\left(\int_{-\infty}^\infty x_2(\tilde{t})e^{-i(\omega-s)\tilde{t}}\,\mathrm{d}\tilde{t}\right)
\,\mathrm{d}s\\
&=\frac{1}{2\pi}\int_{-\infty}^\infty\int_{-\infty}^\infty
x_1(t)x_2(\tilde{t})e^{-i\omega\tilde{t}}
\left(\int_{-\infty}^\infty e^{-is(t-\tilde{t})}\,\mathrm{d}s\right)
\,\mathrm{d}t\,\mathrm{d}\tilde{t}\\
&=\int_{-\infty}^\infty\int_{-\infty}^\infty
x_1(t)x_2(\tilde{t})e^{-i\omega\tilde{t}}
\delta(t-\tilde{t})
\,\mathrm{d}t\,\mathrm{d}\tilde{t}\\
&=\int_{-\infty}^\infty
x_1(t)x_2(t)e^{-i\omega t}
\,\mathrm{d}t.
\end{aligned}
```

And we do indeed see that this is the Fourier Transform of
$y(t)=x_1(t)x_2(t)$.^[In the second-to-last line of the derivation we have used
$\frac{1}{2\pi}\int_{-\infty}^{\infty} e^{ix(a-b)}\,\mathrm{d}x
=\delta(a-b)$.]
The proof of the reverse case is obtained in a similar fashion.
