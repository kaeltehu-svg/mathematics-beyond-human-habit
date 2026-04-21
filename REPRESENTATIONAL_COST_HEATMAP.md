# Representational Cost Heatmap

![Representational Cost Heatmap](./docs/figures/representational_cost_heatmap.png)

## What this shows

This heatmap visualizes how the same integer changes in representational cost when written in different numeral bases.

- Each **row** is a number from **1 to 128**
- Each **column** is a base from **2 to 16**
- Each **cell color** encodes the **digit-length** of that number in that base

The represented number does not change.  
Its representation does.

---

## Core point

The heatmap makes one fact immediately visible:

**the number stays the same, but its representational cost changes with the base.**

A number is invariant.  
Its encoding is not.

This matters because many systems treat a chosen representation as if it were neutral. It is not. Even for something as basic as integer notation, descriptive cost depends on the lens.

---

## Example

Take the number **128**:

- In **base 2**: `10000000` -> **8 digits**
- In **base 10**: `128` -> **3 digits**
- In **base 16**: `80` -> **2 digits**

Same number.  
Different representations.

This is not a semantic effect.  
It is a structural effect induced by the representational system.

---

## Why the diagonal bands appear

The diagonal bands are not decoration. They are the visible signature of threshold changes in digit-length across bases.

For a fixed base `b`, the number of digits needed to write `n` changes when `n` crosses powers of `b`:

- 1 digit for `1 <= n < b`
- 2 digits for `b <= n < b^2`
- 3 digits for `b^2 <= n < b^3`
- and so on

Because each base partitions the same numeric interval differently, the boundaries shift from column to column. The result is a family of diagonal transition bands.

---

## Interpretation

This figure does **not** prove a full theory by itself.

What it does show, clearly and without ambiguity, is:

1. the underlying number is stable
2. the descriptive burden is not
3. representational choice introduces measurable structural variation

That is the only claim this figure needs to make.

---

## Minimal takeaway

**Representation is relative.  
The number is invariant.  
The representational cost is not.**

---

## Relation to OMNIABASE

This figure is a minimal visual entry point into the OMNIABASE direction.

OMNIABASE begins from a simple question:

**what remains invariant, and what changes, when the same object is observed through multiple bases?**

This heatmap shows the first irreducible fact behind that question:

**base choice changes representation even when the object does not change.**

That does not yet solve the larger problem.  
But it exposes the problem cleanly.

---

## Suggested placement

Recommended image path:

```text
/docs/figures-representational_cost_heatmap.png
