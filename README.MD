# Functional Programming Exercises in Racket

Small university project containing a collection of functional-programming and numerical-computation exercises written in Racket.

> **Academic project**
>
> This repository is not a complete application or reusable library. It has no command-line interface, graphical interface, automated test suite, packaged API, or executable workflow. It is mainly useful for reading the implementations and evaluating the functions interactively in DrRacket.

## Reconstructed assignment

The original assignment brief is not included in the repository. Based on the implemented procedures, the project appears to cover exercises from Chapter 1 of *Structure and Interpretation of Computer Programs* (SICP), especially Exercises 1.4, 1.5 and 1.35–1.38.

This reconstruction is inferred from the source code and should not be considered the official assignment text.

## What the project demonstrates

The file [`laai2_racket.rkt`](laai2_racket.rkt) includes examples of:

- applicative-order evaluation and deliberate non-termination;
- higher-order procedures, including selecting an arithmetic operator at runtime;
- fixed-point iteration with a configurable numerical tolerance;
- approximation of the golden ratio;
- solving equations of the form `x^x = n`, with and without average damping;
- recursive and iterative evaluation of finite continued fractions;
- approximation of `1 / φ` and Euler's number through continued fractions.

Although the source uses `#lang gamble` and imports `gamble/viz`, it does not define probabilistic models or use Gamble's inference features. The implemented exercises rely on ordinary functional and numerical operations.

## Requirements

- [Racket](https://racket-lang.org/)
- [Gamble](https://rmculpepper.github.io/gamble/), required by the module declaration

Install the Gamble package with:

```bash
raco pkg install gamble
```

## Running the exercises

Open `laai2_racket.rkt` in DrRacket and select **Run**. The file only defines procedures, so it does not produce a complete result automatically. Call the desired functions from the interactions window.

Examples:

```racket
(a-plus-abs-b 5 -3)
; 8

(golden-ration-fixed-point)
; prints the intermediate guesses and converges to approximately 1.618

(log-no-avg 1000)
(log-with-avg 1000)
; compare fixed-point convergence with and without average damping

(one-over-gr-appr-rec 11)
(one-over-gr-appr-iter 11)
; approximately 0.618

(+ 2 (de-fractionibus-continuis 10))
; approximately 2.7182817
```

## Important caveat

The procedure `p` is intentionally recursive without a base case. Evaluating the following expression under Racket's eager evaluation strategy does not terminate:

```racket
(test 0 (p))
```

This behavior is part of the evaluation-order experiment, not a general-purpose function.

## Repository contents

- `laai2_racket.rkt` — exercise implementations;
- `laai2_racket.bak` — an older editor backup containing only the initial evaluation-order example.

## Limitations

- the original assignment text is missing;
- there is no main program or interactive menu;
- the functions are not exposed as a documented library;
- there are no automated tests;
- the project imports Gamble but does not use probabilistic programming;
- some identifiers retain spelling mistakes from the original coursework, such as `tollerance` and `golden-ration-fixed-point`.
