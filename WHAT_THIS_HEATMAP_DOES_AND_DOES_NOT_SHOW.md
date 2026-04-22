# What This Heatmap Does and Does Not Show

![Representational Cost Heatmap](./docs/figures/representational_cost_heatmap.png)

## Purpose

This note separates two different things:

1. what mathematics already knew
2. what may become genuinely new if representation-change is used as a structural measurement tool

This distinction matters.

Without it, the figure risks being overstated.

---

## What the heatmap shows

The heatmap visualizes the same integers across multiple numeral bases.

- Each **row** is a number from **1 to 128**
- Each **column** is a base from **2 to 16**
- Each **cell color** encodes the **digit-length** of that number in that base

So the figure is not showing the number itself changing.

It is showing that the **representational cost** of the same number changes with the base.

In the most compact form:

**the number is invariant,  
the representation is not.**

---

## What the world already knew

The world already knew that the same integer can be written in different bases.

It already knew that:

- the written form changes with the base
- the number of digits changes with the base
- lower bases often require longer representations
- higher bases often compress the same value into fewer digits

This is standard mathematics.

For a positive integer `n`, the number of digits in base `b` is governed by the usual logarithmic relation:

```text
digits_b(n) = floor(log_b(n)) + 1

So the basic fact that representation-length changes across bases is not new.

This figure does not discover that fact.

It makes that fact visible.

That is valuable, but it must be stated correctly.


---

What the diagonal bands mean

The diagonal bands are not decorative.

They are the visible trace of digit-length thresholds across bases.

For a fixed base b, the number of digits changes when n crosses powers of b:

1 digit for 1 <= n < b

2 digits for b <= n < b^2

3 digits for b^2 <= n < b^3

and so on


Because each base partitions the same interval differently, those thresholds shift from column to column.

That shifting creates the diagonal transition bands.

So the heatmap is a compact visualization of a simple but important structural fact:

the descriptive burden depends on the representational system.


---

Example

Take the number 128.

In base 2: 10000000 -> 8 digits

In base 10: 128 -> 3 digits

In base 16: 80 -> 2 digits


Same number.
Different representations.

Nothing semantic is happening here.

The variation is induced entirely by the representational system.


---

What this figure does NOT prove

This figure does not prove a new theory by itself.

It does not show that mathematics was wrong.

It does not establish a complete multibase framework.

It does not identify a final structural invariant.

It does not yet prove that OMNIABASE is valid as a full research program.

Those stronger claims require formalization, definitions, metrics, and falsifiable tests.

This image alone is not enough.


---

What may be genuinely new

The possible novelty does not lie in the fact that representations differ across bases.

That part was already known.

The possible novelty begins only if representation-change is turned into a systematic measurement tool.

That means asking questions such as:

Which properties remain stable across many bases?

Which properties drift strongly under base change?

Which apparent patterns exist only in one representation?

Which regularities survive representational variation?

Can cross-base stability be measured explicitly?

Can representational drift be quantified?


This is the real frontier.

The move is from:

multiple representations as notation

to:

multiple representations as structural probes

That is the possible shift from known mathematics to new method.


---

The central new hypothesis

A possible new claim is the following:

variation across representations is not just a nuisance to ignore; it can be used as measurable signal.

And more strongly:

a property that survives many representations has stronger structural status than a property that appears only in one encoding.

If this can be formalized and tested, then base variation stops being just a notational fact and becomes a method for structural discrimination.

That is where new information may emerge.


---

The honest separation

Already known

the same number admits multiple base representations

the written form changes with the base

digit-length changes with the base

these changes follow known mathematical rules


Potentially new

using cross-base variation as a measurement device

defining invariance across bases as a structural criterion

distinguishing object-properties from encoding-artifacts

measuring representational drift

treating base change as a robustness test rather than a re-expression step


This distinction must remain explicit.

Otherwise a visual clarification gets confused with a discovery claim.


---

Why this matters

Many systems behave as if a chosen representation were neutral.

It is not.

This figure is a minimal demonstration of that non-neutrality.

If even integer notation changes descriptive cost under representational change, then treating one encoding as if it were the object itself is logically weak.

The object and its description must be separated.

That separation is the real conceptual value of this heatmap.


---

Minimal conclusion

The heatmap does not discover a new elementary fact.

It may open a new use of an old fact.

That use would be this:

change the representation, then measure what remains and what moves.

If pursued rigorously, that is the beginning of a structural method.


---

Compressed takeaway

What was already known?
Representation changes with the base.

What may be new?
Using that change as a tool to measure structural stability, drift, and invariance.


---

Relation to OMNIABASE

In OMNIABASE terms, this heatmap should be treated as a minimal entry point, not as a final result.

It shows the first irreducible fact:

base choice changes representational cost even when the object does not change.

That alone is not the full theory.

But it establishes the problem cleanly.

And any serious multibase framework must begin there.

Nel `README.md` metterei solo una riga secca:

```markdown
For a precise explanation of what the heatmap shows, and what it does not, see [WHAT_THIS_HEATMAP_DOES_AND_DOES_NOT_SHOW.md](./WHAT_THIS_HEATMAP_DOES_AND_DOES_NOT_SHOW.md).

