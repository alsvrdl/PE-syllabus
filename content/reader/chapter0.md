# Chapter 0 - Fourier Transforms

## Introduction

In this chapter you will learn to apply the mathematical method of
Fourier analysis to physics research. The big conceptual step that you
need to make is to describe time-dependent signals in the frequency
domain by thinking of these signals as being composed of infinitely many
harmonic functions. Instead of thinking about the signal and the
response of a physical system as a function of time, you will learn to
think about signals and physical quantities as an amplitude and phase in
the frequency domain. With time you will appreciate the frequency domain
as it allows to analyze the response of a system one frequency at a
time. This is a much easier problem than dealing with all frequencies at
once. More importantly, it is often possible to develop some intuition
in the frequency domain or to zoom in on a small effect at a particular
frequency on top of a large background. For instance, we know that a
harmonic oscillator or pendulum tends to oscillate at its natural
frequency.

Another good example is given by
figure [1](#figure1){reference-type="ref" reference="figure1"} that
looks like a sinusoidal wave with some additional higher frequency
component on top of the signal. The same signal in the frequency domain
reveals a large amplitude, low frequency peak and a second higher
frequency peak with a smaller amplitude.

<figure id="figure1">
<div class="center">
<img src="figures/figure1.png" />
</div>
<figcaption> An example of the use of Fourier analysis with intensity
plotted in the time domain (left) and frequency domain (right). The
frequency domain plot clearly reveals that the signal contains a slow
and fast oscillation. (Image from <a
href="https://lstsal.wordpress.com/2015/02/28/comparing-two-audio-files/"
class="uri">https://lstsal.wordpress.com/2015/02/28/comparing-two-audio-files/</a>)
</figcaption>
</figure>

## Linear systems 

The underlying reason why the method of Fourier analysis is so
successful is that most physical phenomena are linear: If we increase
the input (or stimulus) by a constant factor then the output (or
response) of the system increases by that same constant factor. Many
real-world systems respond in some way to stimuli, and are characterized
by an input-output relationship. An electrical system, such as an
amplifier in a stereo set, is an example of such a system -- it has
signal inputs from CD players, radio, etc., and outputs to speakers.
This is an example of a 'linear system', because its output is
proportional to the input. The system may become nonlinear if you
turn-up the amplifier way to loud and saturate the output. This produces
sound waves that have their tops chopped off because there is a limit to
how much power the amplifier can generate. You may hear different sounds
than were on the original recording if the volume is too high (they tend
to be screechy).

Linear systems can be more complicated than an amplifier, however. The
general definition of a linear system is any system whose output $F(x)$
satisfies the following equation: 
$$F(a~g(t) + b~h(t)) = a~F(g(t)) + b~F(h(t))$$ 
where $a$ and $b$ are
constant real numbers. The functions $g(t)$ and $h(t)$ are arbitrary
functions of an independent variable $t$ (commonly time is used a
independent variable in applications, but it can also be a position).
The definition shows that constant multiplicative scale factors can be
'factored-out'. More importantly, it tells us that the response of a
linear system to a sum of inputs is the sum of the responses to each
individual input separately.

## Examples of linear systems {#examples-of-linear-systems .unnumbered}

1.  Wave propagation such as sound waves or electromagnetic waves

2.  Electrical circuits composed of resistors, capacitors and inductors.
    These circuits can be designed as a frequency filter that only
    passes low frequencies and reject high, or vice-versa.

3.  Mechanical motion of masses with springs and dashpots (to include
    damping)

4.  Limiting cases of non-linear systems for small inputs are linear:
    Even if the output of a system is not exactly linear, it will often
    be approximately linear for small enough inputs.

5.  Most optical systems are linear -- lenses and optical fibers all
    have linear responses to how much light is put in. They may distort
    the input light in other ways (delays, changing the angle depending
    on color), but they are described by the linear equations above.
    Some optical systems are non-linear: for instance they change the
    frequency of the light that comes in (fluorescent materials for
    example).

6.  The process of differentiation and integration are both linear
    systems

7.  A convolution as a mathematical operation where each value in the
    output is expressed as a sum of values in the input multiplied by a
    set of weighing coëfficients. This operation plays an important role
    if one samples an ideal signal using a measurement apparatus with a
    finite resolution, e.g. the finite response time (inverse bandwidth)
    of an oscilloscope or the point-spread function of a telescope.

Fourier analysis can be used to construct the output of a linear system
to an arbitrary input by thinking of this input as a sum of harmonic
functions. This is a very powerful and useful method if the input-output
relation for harmonic functions is easier to obtain and if we have a
general method that can decompose an arbitrary function as a sum of
harmonic functions.
