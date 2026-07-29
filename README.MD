# Functional Programming and Numerical Methods in Racket

University project developed for the second **Languages and Applications for Artificial Intelligence** assignment.

The assignment consists of implementing a selection of exercises from Chapter 1 of *Structure and Interpretation of Computer Programs* (SICP), with particular focus on evaluation strategies, higher-order procedures, fixed-point iteration and continued fractions.

## Assignment

The project covers SICP Exercises **1.4, 1.5 and 1.35–1.38**:

- defining an arithmetic procedure that selects an operator at runtime;
- analysing applicative-order evaluation through a deliberately non-terminating procedure;
- approximating the golden ratio with fixed-point iteration;
- comparing convergence with and without average damping;
- implementing finite continued fractions using recursive and iterative processes;
- approximating the inverse golden ratio and Euler's number.

## Implemented exercises

All implementations are contained in [`laai2_racket.rkt`](laai2_racket.rkt).

### Operator selection

`a-plus-abs-b` computes `a + |b|` by choosing either addition or subtraction as a first-class procedure.

```racket
(a-plus-abs-b 5 -3)
; 8
```

### Evaluation order

The procedures `p` and `test` reproduce the evaluation-order example from SICP Exercise 1.5.

```racket
(define p (lambda () (p)))

(define (test x y)
  (if (= x 0) 0 y))
```

Evaluating `(test 0 (p))` under Racket's applicative-order evaluation does not terminate because the argument `(p)` is evaluated before `test` is applied.

### Fixed-point iteration

The generic `fixed-point` procedure repeatedly applies a function until two consecutive values differ by less than the configured tolerance.

It is used to:

- approximate the golden ratio;
- solve equations of the form `x^x = n`;
- compare convergence with and without average damping.

```racket
(golden-ration-fixed-point)

(log-no-avg 1000)
(log-with-avg 1000)
```

The procedure prints each intermediate approximation, making the convergence process directly observable.

### Continued fractions

Finite continued fractions are implemented in two ways:

- `cont-frac-rec`, using a recursive process;
- `cont-frac-iter`, using an iterative process.

They are used to approximate the inverse golden ratio:

```racket
(one-over-gr-appr-rec 11)
(one-over-gr-appr-iter 11)
; approximately 0.618
```

The `de-fractionibus-continuis` procedure implements Euler's continued-fraction expansion for `e - 2`:

```racket
(+ 2 (de-fractionibus-continuis 10))
; approximately 2.7182817
```

## Requirements

- [Racket](https://racket-lang.org/)
- [Gamble](https://rmculpepper.github.io/gamble/)

Install Gamble through Racket's package manager:

```bash
raco pkg install gamble
```

## Running the project

Open [`laai2_racket.rkt`](laai2_racket.rkt) in DrRacket and select **Run**. The procedures can then be evaluated from the interactions window.

Alternatively, run the file from a terminal:

```bash
racket laai2_racket.rkt
```

Since the source file defines procedures without invoking them automatically, call the desired functions from DrRacket or add temporary expressions at the end of the file.

## Repository contents

- `laai2_racket.rkt` — complete implementation of the assignment;
- `laai2_racket.bak` — earlier backup of the initial evaluation-order exercise.
