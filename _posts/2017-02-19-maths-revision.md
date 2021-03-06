---
layout: post
title: Pieces of mathematics
date: '2017-02-19'
author: Monik
tags:
- Maths
commentIssueId: 35
---
<div class="bg-info panel-body" markdown="1">
Pieces of mathematics that are relevant for a developer.
</div>

<h3>Table of contents</h3>
- TOC
{:toc max_level=1}

<!-- http://docs.mathjax.org/en/latest/start.html -->

## Summations

This is called a summation, more specifically arithmetic progression:

<math xmlns="http://www.w3.org/1998/Math/MathML">
    <munderover>
      <mo>&sum;</mo>
      <mn>i=1</mn>
      <mn>n</mn>
    </munderover>
    <mn>i</mn>
    <mo>=</mo>
    <mfrac><mi>n(n+1)</mi><mn>2</mn></mfrac>
</math>

because mathematical induction. Important to remember, as this means that the complexity of an algorithm that takes `i` steps with every iteration from `i=0..n` has complexity of `Θ(n^2)` (big theta). This is the case of **selection sort**. And the generified rule is:

<math xmlns="http://www.w3.org/1998/Math/MathML">
    <mi>S(n, p)</mi>
    <mo>=</mo>
    <munderover>
      <mo>&sum;</mo>
      <mi>i</mi>
      <mi>n</mi>
    </munderover>
    <msup>
      <mi>i</mi>
      <mi>p</mi>
    </msup>
    <mo>=</mo>
    <mi>Θ(</mi>
    <msup>
         <mi>n</mi>
         <mi>p+1</mi>
    </msup>
    <mi>)</mi>
</math>

for `p>=1`.

Geometric series have the index of the loop involved in the exponent:

<math xmlns="http://www.w3.org/1998/Math/MathML">
    <mi>G(n, a)</mi>
    <mo>=</mo>
    <munderover>
      <mo>&sum;</mo>
      <mi>i=0</mi>
      <mi>n</mi>
    </munderover>
    <msup>
      <mi>a</mi>
      <mi>i</mi>
    </msup>
    <mo>=</mo>
    <mfrac>
        <mrow>
            <msup>
              <mi>a</mi>
              <mi>n+1</mi>
            </msup>
            <mo>-</mo>
            <mn>1</mn>
        </mrow>
        <mrow>
            <mi>a</mi>
            <mo>-</mo>
            <mn>1</mn>
        </mrow>
    </mfrac>
    <mo>=</mo>
    <mi>Θ(</mi>
    <msup>
         <mi>a</mi>
         <mi>n+1</mi>
    </msup>
    <mi>)</mi>
</math>

for for `a>1`.

What may be also relevant is this factorial formula:

<math xmlns="http://www.w3.org/1998/Math/MathML">
    <munderover>
      <mo>&sum;</mo>
      <mi>i=1</mi>
      <mi>n</mi>
    </munderover>
    <mi>i</mi>
    <mo>*</mo>
    <mi>i</mi>
    <mo>!</mo>
    <mo>=</mo>
    <mi>(n+1)!-1</mi>
</math>

## Logarithms

This is what logarithm is:

b<sup>x</sup> = y <=> log <sub>b</sub> y = x

| Important formulas                |
|-----------------------------------|
|e<sup>ln x</sup> = x               |
|b<sup>log<sub> b</sub> y</sup> = y |
|log<sub>a</sub>(x*y) = log<sub>a</sub>(x) + log<sub>a</sub>(y) |
|a<sup>b</sup> = e<sup>ln(a^b)</sup> = e<sup>b*ln(a)</sup> |

The last one can be used for computing a<sup>n</sup> fast. We just make a recursive function that will compute the squares or "squares + 1" of the previous result, and that is just O(`lg(n)`).

<math xmlns="http://www.w3.org/1998/Math/MathML">
    <msub>
        <mi>log</mi>
        <mi>a</mi>
    </msub>
    <mi>b</mi>
    <mo>=</mo>
    <frac>
        <mrow>
            <msub>
                <mi>log</mi>
                <mi>c</mi>
            </msub>
            <mi>b</mi>
        </mrow>
        <mrow>
            <msub>
                <mi>log</mi>
                <mi>c</mi>
            </msub>
            <mi>a</mi>
        </mrow>
    </frac>
</math>

Harmonic summation is another important formula:

<math xmlns="http://www.w3.org/1998/Math/MathML">
    <munderover>
      <mo>&sum;</mo>
      <mi>i=1</mi>
      <mi>n</mi>
    </munderover>
    <frac>
      <mn>1</mn>
      <mi>i</mi>
    </frac>
    <mo>≈</mo>
    <mi>ln(n)</mi>
</math>

## Quadratic Equation

Square roots of quadratic equation:

- `d = sqrt(b`<sup>`2`</sup>`-4ac)`
- `x = (-b +/- d)/2a`

## Trygonometry

Area of a triangle:

- `1/2 * a * h`, `h` is the height of the triangle measured from `a`
- `1/2 * a * b * sin(α)`, `α` is the angle between `a` and `b`

## Prime numbers

_Every positive integer can be decomposed into a product of primes_.

[Sieve of Eratosthenes](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes) is an algorithm to fins all prime numbers up to a given
**max** value: in a sorted list starting from `2` we take each number and count it as prime, and cross out all following numbers that are divisible by this number.

We can also ask for testing whether a [number is prime](https://en.wikipedia.org/wiki/Primality_test).

## Combinatorics

- Number of possible **permutations** of `n` elements: `n!`
- Number of possible **variations** of `k` distinct elements from `n` (order matters): `n!/(n-k)!`
- Number of possible **variations** of `k` elements from `n` (order matters): `n^k`
- Number of possible **combinations** of `k` distinct elements from `n` (order does not matter): `n!/k!(n-k)!` (Newton's symbol)
- Number of possible **combinations** of `k` elements from `n` (order does not matter): `(n+k-1)!/k!(n-1)!`

## Probability

What is the probability that out of 3 consecutive tries 2 are successful, if each try has probability _p_ of being successful?

Answer: `p*p*(1-p)`.

### Conditional probability

- `P(A and B) = P(B given A)*P(A)`
- `P(A or B) = P(A) + P(B) - P(A and B)`

But:

For A and B independent (A happening tells me nothing about B happening):

- `P(A and B) = P(A) * P(B)`

For A and B mutually exclusive (if A happens B cannot happen:

- `P(A or B) = P(A) + P(B)`

*Only impossible events are both mutually exclusive and independent.
