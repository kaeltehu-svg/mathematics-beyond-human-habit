# OMNIABASE Protocol v0

## A minimal measurement protocol for cross-base structural observation

## Status

This document defines the first minimal operational protocol for OMNIABASE.

Its purpose is not to solve the full problem.

Its purpose is to convert the core idea into a reproducible measurement procedure.

The central question is:

**given the same integer observed across multiple bases, which measured properties remain stable, which drift, and which collapse?**

---

## 1. Scope

This protocol applies only to:

- finite positive integers
- observed through standard positional numeral systems
- over a fixed finite base interval

This is a deliberately narrow starting point.

It avoids semantic ambiguity and keeps the first protocol fully explicit.

---

## 2. Observation domain

### Objects

The observed objects are integers:

```text
n in {1, 2, 3, ..., N}

where N is chosen in advance.

Initial recommended range:

N = 128

This range is small enough to inspect directly and large enough to show visible cross-base variation.

Admissible representations

Each integer is represented in every base:

b in {2, 3, 4, ..., 16}

So the representational family for a number n is:

R(n) = { repr_b(n) | b in {2, ..., 16} }

where repr_b(n) is the standard positional representation of n in base b.

This family is the observational orbit of n under admissible base change.


---

3. Minimal observed properties

For each pair (n, b), compute the representation of n in base b and measure the following properties.

P1. Digit-length

L(n, b) = number of digits in repr_b(n)

This is the most basic representational cost measure.

P2. Digit-sum

S(n, b) = sum of digits in repr_b(n)

This captures how digit mass is distributed across bases.

P3. Zero count

Z(n, b) = number of zero digits in repr_b(n)

This tracks internal sparsity of the representation.

P4. Trailing zero count

T(n, b) = number of trailing zeros in repr_b(n)

This captures divisibility-alignment effects between n and b.

P5. Symbol diversity

D(n, b) = number of distinct symbols appearing in repr_b(n)

This is a minimal heterogeneity measure.

P6. Repetition score

Let f_i be the frequency of digit i in the representation.

A minimal repetition score may be defined as:

Rep(n, b) = max_i f_i / L(n, b)

This captures concentration around a dominant symbol.


---

4. Why these properties were chosen

These properties are intentionally simple.

They satisfy four conditions:

1. they are computable for every observed pair (n, b)


2. they are representation-level rather than semantic


3. they are easy to inspect and verify


4. they allow immediate comparison across bases



This is enough for a first protocol.

The goal of v0 is not richness.

The goal of v0 is reproducibility.


---

5. Cross-base profiles

For each integer n, each property induces a profile across bases.

Examples:

L_profile(n)   = [L(n,2), L(n,3), ..., L(n,16)]
S_profile(n)   = [S(n,2), S(n,3), ..., S(n,16)]
Z_profile(n)   = [Z(n,2), Z(n,3), ..., Z(n,16)]
T_profile(n)   = [T(n,2), T(n,3), ..., T(n,16)]
D_profile(n)   = [D(n,2), D(n,3), ..., D(n,16)]
Rep_profile(n) = [Rep(n,2), Rep(n,3), ..., Rep(n,16)]

These profiles are the raw observational outputs of the protocol.


---

6. Invariance and drift

This protocol does not assume that all interesting properties are perfectly invariant.

Instead, it distinguishes several behaviors across the representational family.

6.1 Strictly invariant property

A property P is strictly invariant over the chosen base interval for object n if:

P(n, b) = constant for all b in {2, ..., 16}

This will be rare for representation-level quantities.

6.2 Drift-sensitive property

A property is drift-sensitive if its value changes substantially across bases.

In v0, this is measured by profile spread:

drift_P(n) = max_b P(n, b) - min_b P(n, b)

For real-valued properties, this may be supplemented by standard deviation across bases.

6.3 Collapse-prone property

A property is collapse-prone if an apparent pattern visible in one or more bases disappears in others.

In v0, this is not yet a fully formal class.

It is tracked qualitatively through profile inspection and cross-base comparison.

6.4 Encoding artifact candidate

A measured feature is an encoding artifact candidate if it appears highly salient in one base but does not persist across the representational family.

In v0, this is treated as an interpretive flag, not yet as a theorem.


---

7. Minimal stability scores

For each property profile of each number, define a simple normalized stability score.

For a property P with cross-base values P(n,b), define:

stability_P(n) = 1 / (1 + drift_P(n))

This is only a placeholder normalization for protocol v0.

It has the following properties:

maximum value 1 when drift is zero

decreases as cross-base spread increases

easy to compute and compare


This should not be mistaken for a final metric.

It is only a first operational score.


---

8. Output format

For each integer n, the protocol should produce a structured record containing:

the integer itself

the set of bases used

the representation in each base

the measured property values in each base

the profile for each property

the drift for each property

the stability score for each property


A JSON-like schema:

{
  "n": 128,
  "bases": [2,3,...,16],
  "representations": {
    "2": "10000000",
    "3": "...",
    ...
  },
  "properties": {
    "digit_length": {...},
    "digit_sum": {...},
    "zero_count": {...},
    "trailing_zero_count": {...},
    "symbol_diversity": {...},
    "repetition_score": {...}
  },
  "profiles": {...},
  "drift": {...},
  "stability": {...}
}

This creates a reproducible object-level profile.


---

9. First validation goal

The first validation goal is modest.

It is not to prove a grand theory.

It is to test whether cross-base measurement produces non-trivial and reproducible distinctions between numbers.

The initial validation questions are:

1. Which properties are almost always highly base-sensitive?


2. Which properties show partial stability across many numbers?


3. Which numbers have unusually distinctive cross-base profiles?


4. Which apparent patterns are local to a base and which survive across many bases?



If these questions produce measurable and reproducible answers, the protocol has succeeded as a first methodological step.


---

10. Minimal expected findings

The protocol expects to confirm at least the following:

digit-length is strongly base-sensitive

trailing zeros depend strongly on divisibility relations between number and base

symbol diversity and repetition can change substantially across bases

some numbers may exhibit unusually stable or unstable cross-base signatures


These are not final discoveries.

They are baseline observations that establish whether the protocol is informative.


---

11. Interpretation rule

A property observed in one base must not automatically be treated as intrinsic to the number.

The protocol adopts the following rule:

a property has stronger structural credibility if it persists across the admissible representational family.

Conversely:

a property that appears only in isolated representations must be treated cautiously as a possible encoding artifact.

This rule is the operational heart of OMNIABASE.


---

12. What v0 does not do

Protocol v0 does not yet provide:

a final invariance metric

a general theorem of structural status

a proof that all important structure is cross-base persistent

a canonical weighting of bases

a universal definition of artifact

extension to rationals, reals, algebraic objects, or symbolic formulas


Those belong to later stages.

v0 is only the first operational scaffold.


---

13. Recommended first implementation

The recommended first implementation is:

integers 1..128

bases 2..16

full computation of all six properties

export of one machine-readable results file

one human-readable summary file with main observations

at least one visual summary per property family


This is enough to test whether the protocol yields structured information.


---

14. Recommended repository outputs

Suggested files:

examples/omnia_protocol_v0_numbers_1_128.jsonl
docs/OMNIABASE_PROTOCOL_v0_RESULTS.md
docs/figures/representational_cost_heatmap.png
docs/figures/digit_sum_heatmap.png
docs/figures/zero_count_heatmap.png

These are only recommended names.

The key point is to preserve reproducibility.


---

15. Minimal conclusion

OMNIABASE Protocol v0 defines the first reproducible procedure for observing the same integer across multiple bases and measuring how selected properties behave under representational change.

Its purpose is not to complete the theory.

Its purpose is to create a minimal bridge from concept to measurement.

That bridge is the first necessary condition for anything stronger.