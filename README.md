# Introduction to Probability 

## Statistics vs. Probability

- **Statistics**: the science of using data effectively to gain new knowledge — collecting and analyzing data *ethically*, meaning in accordance with the hypotheses/assumptions of the statistical tests being used.
- **Population**: the individuals or objects from which we want to acquire information or draw a conclusion. Usually too large (or even hypothetical) to observe fully.
- **Sample**: a subset of the population that we actually collect data on.
- **Probability vs. Statistics — the key contrast**:
  - *Probability*: we assume we already know the characteristics of the entire population, and we ask what we can say about a sample drawn from it.
  - *Statistics*: works in reverse — given a sample with certain characteristics, we ask (with some degree of confidence) whether the whole population shares that characteristic.
  - Course sequence: learn probability first (population → sample), then statistics (sample → population).

## Why Probability?

Probability gives randomness and uncertainty a mathematical foundation, e.g.:

- Probability of getting at least two heads in five coin flips.
- Probability a customer buys milk given they're buying bread.
- Probability a stock price falls in a certain range by a certain date.

## Core Terminology

| Term | Definition |
|---|---|
| **Experiment** | Any action or process that generates observations. |
| **Sample space (S)** | The set of *all* possible outcomes of an experiment. |
| **Event** | A single outcome, or a collection of outcomes, from the experiment. |
| **Cardinality** \|S\| | The number of outcomes contained in a sample space or event. |

## Worked Examples of Sample Spaces

1. **Flip a coin once** → S = {0, 1} (0 = head, 1 = tail). \|S\| = 2.
2. **Flip a coin twice** → S = {HH, HT, TH, TT}. \|S\| = 4.
3. **Flip a coin until you get a tail** → S = {T, HT, HHT, HHHT, …} — continues indefinitely (a run of all heads has vanishingly small but nonzero probability). \|S\| = ∞.
4. **Inspect a car for 3 defects** (engine, seat belt, paint — each present/absent, coded as a 3-digit binary string):
   S = {000, 100, 010, 001, 110, 101, 011, 111}. \|S\| = 8.

## Set Notation for Events

Given two events A and B:

- **A ∪ B (union)**: outcomes that are in A *or* in B (combined together).
- **A ∩ B (intersection)**: outcomes that are in A *and* in B.
- **Aᶜ (complement)**: all outcomes in S that are *not* in A.
- **Mutually exclusive / disjoint**: A and B share no outcomes, i.e. A ∩ B = ∅.

### Applied to the car-defect example (S from example 4 above; digit order = engine, seat belt, paint)

- **A** = engine problem present = {100, 110, 101, 111}
- **B** = exactly one defect = {100, 010, 001}
- **C** = exactly two defects = {110, 101, 011}

Derived events:

- **A ∩ B** = {100}
- **Aᶜ** = {000, 010, 001}
- **Aᶜ ∪ B** = {000, 010, 001, 100}
- **B ∩ C** = ∅ (empty set — B and C are mutually exclusive)

## Venn Diagrams

- Used to visualize unions, intersections, and complements.
- The rectangle = the full sample space S; circles = individual events.
- Every outcome in S belongs in exactly one region of a correctly drawn Venn diagram (no overlaps missed, nothing double-counted).
- Example placement using A, B, C above:
  - A ∩ B → 100
  - B ∩ C → ∅ (empty)
  - A ∩ C → {110, 101}
  - Only in C → 011
  - Only in B → {010, 001}
  - Only in A → 111
  - In none of A, B, C → 000

## Takeaway

This module sets up the vocabulary (experiment, sample space, event, cardinality) and set operations (union, intersection, complement, disjoint) needed before moving on to the axioms of probability and predicting experimental outcomes in later videos.

Next lecture in this series: extending this framework to conditional probability.


