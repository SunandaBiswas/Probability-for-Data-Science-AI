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


## Counting: Permutations and Combinations
Notes from the Coursera lecture "Counting: Permutations and Combinations" — part of Probability Theory: Foundation for Data Science.


## 1. Why we need counting
Probability theory starts with assigning a number P(A) — the chance that event A occurs.

If a sample space S consists of N equally likely simple events E₁, E₂, …, E_N, each event has probability 1/N. For any subset A ⊆ S:

P(A) = (number of simple events in A) / N

So when outcomes are equally likely, computing a probability reduces to counting outcomes. That's what permutations and combinations are tools for.
Worked example — rolling two dice
Roll a fair six-sided die twice. The sample space consists of ordered pairs (i, j), where i is the first roll and j is the second. Since each die has 6 outcomes, |S| = 36, and every outcome is equally likely.

A = "first roll is a 1": outcomes (1,1) … (1,6) → 6 outcomes → P(A) = 6/36 = 1/6
B = "the two rolls sum to 8": (2,6), (3,5), (4,4), (5,3), (6,2) → 5 outcomes → P(B) = 5/36
C = "second roll is exactly 2 more than the first": (1,3), (2,4), (3,5), (4,6) → 4 outcomes → P(C) = 4/36 = 1/9

## 2. Permutations — order matters
Definition: An ordered sequence of k objects chosen from a set of n objects is a permutation of size k. Order matters — swapping two chosen objects gives a different permutation.

Notation: P(k, n) (also written P_{k,n} or ₙPₖ)

Formula:

P(k, n) = n × (n-1) × (n-2) × … × (n-k+1) = n! / (n-k)!
Worked example — electing officers
An organization has 60 members. Choose a president, a vice president, and a treasurer (3 distinct roles, no repeats).

60 choices for president
59 remaining choices for vice president
58 remaining choices for treasurer

P(3, 60) = 60 × 59 × 58 = 60! / 57! = 205,320

This is a permutation because who gets which role matters — picking Alice as president and Bob as VP is different from Bob as president and Alice as VP.

Reminder — factorials: n! = n × (n-1) × (n-2) × … × 1, and by convention 0! = 1.


## 3. Combinations — order doesn't matter
Definition: An unordered subset of size k chosen from n distinct objects is a combination.

Notation: C(k, n), or more commonly n choose k, written (n k) or ₙCₖ

Formula:

C(n, k) = n! / (k! × (n-k)!)
Where the formula comes from
Take the same 60-person example, but now just pick a team of 3 (no distinct roles — order doesn't matter).

Every unordered team of 3 people corresponds to 3! = 6 different ordered permutations (the 3 people can be arranged into president/VP/treasurer in 6 ways). So the permutations "collapse" into combinations by grouping them in sets of 3!:

C(60, 3) = P(3, 60) / 3! = 60! / (3! × 57!)

This ratio comes up constantly, hence the dedicated notation 60 choose 3.

General form:

n choose k = n! / (k! (n-k)!)

Symmetry property: n choose k = n choose (n-k). Choosing 3 people to be on a team is equivalent to choosing the 57 people left out — both describe the same split of the group, so 60 choose 3 = 60 choose 57.

## 4. Permutations vs. Combinations — quick comparison


Permutation
Combination
Order matters?
Yes
No
Notation
P(k, n)
n choose k
Formula
n! / (n-k)!
n! / (k!(n-k)!)
Example use
President / VP / Treasurer
Picking a team/committee

## 5. Worked example — committee with composition constraints
Same group of 60 people: 35 women and 25 men. Select a committee of 11 people.

Total number of possible committees (sample space size): 60 choose 11
Each committee is assumed equally likely.

Question: What is the probability the committee has at least 5 men and at least 5 women?

With 11 total seats, "at least 5 of each" only leaves two possible splits: 5 men & 6 women, or 6 men & 5 women.

P(at least 5 men and at least 5 women)

  = P(5 men, 6 women) + P(6 men, 5 women)

  = [ (25 choose 5)(35 choose 6) + (25 choose 6)(35 choose 5) ] / (60 choose 11)

Each term in the numerator multiplies two independent combination counts — choosing men from the pool of men, and women from the pool of women — because these are independent sub-selections that together make up the committee.

## 6. Worked example — quality inspection (buses)
A city has 20 buses; after inspection, 8 are found to have visible cracks (12 do not). A sample of 5 buses is chosen at random for further inspection.

Sample space size: 20 choose 5 (buses are treated as distinguishable)

P(exactly 4 of the 5 sampled buses have cracks):

P(exactly 4 cracked) = (12 choose 1)(8 choose 4) / (20 choose 5)

(Choose 1 from the 12 non-cracked buses, and 4 from the 8 cracked buses.)

P(at least 4 of the 5 sampled buses have cracks):

This adds the case of all 5 being cracked:

P(at least 4 cracked) = [ (12 choose 1)(8 choose 4) + (12 choose 0)(8 choose 5) ] / (20 choose 5)

This mirrors the committee problem — same "at least" logic, same technique of splitting into mutually exclusive cases and summing their probabilities.

## 7. Key takeaways
Equally-likely sample spaces turn probability problems into counting problems.
Permutations count ordered arrangements — use when roles/positions are distinct: P(k,n) = n!/(n-k)!
Combinations count unordered selections — use when you just need a group: n choose k = n!/(k!(n-k)!)
A combination count can always be derived from a permutation count by dividing out the k! orderings within each group.
For "at least" / "at most" type probability questions with sub-groups (e.g., men/women, cracked/not cracked), break the event into mutually exclusive cases, compute each with a product of combinations (one factor per subgroup), sum the cases, and divide by the total sample space size.



Next lecture in this series: extending this framework to conditional probability.


