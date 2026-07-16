# ADR-0004: DNA + G4 DNA — region-dependent encoding (Laplacian backbone + Klein-4 chirality)

**Status:** Accepted.
**Date:** 2026-07-16.
**Authors:** Steven Kirkland + Claude Opus 4.8 (1M context).
**Supersedes:** none.
**Superseded-by:** none.

---

## 1. Context

Building the fiber atom, the reflex was *"encode everything as Klein-4."* The user
checked it:

> *"why is klein4 better than laplacian for G4 encoded regions? does biology change
> encoding types for G4 DNA?"*

Biology **does** change encoding type by region. The relational double-helix
backbone is **B-DNA**; at regulatory sites it folds into a **G-quadruplex (G4)** —
a four-way structure. Not every region is G4, and G4 is not *"better than"* the
backbone. They are **different regions / reads of one molecule**.

## 2. Decision

One genome carries **both** encodings, **region-dependent**:

- **Laplacian metric** — the relational backbone, **Abelian** → the **B-DNA**
  analogue ("what it's like", the edges read of ADR-0002).
- **Klein-4 / (γ₅, iω₇) four-way chirality** — the ordered *charge* → the **G4 DNA**
  analogue (the G-quadruplex; the ordered fiber / responsion read of ADR-0002).

The **directed genome already carries both** — a *metric* (relational) part and a
*charge* (chirality) part (F1228). Which one is read depends on the region / the
question, exactly as biology folds B-DNA ↔ G4 by region. **Neither is privileged:**
Klein-4 is the sector encoding for the *ordered* read; the Laplacian is the
*relational* backbone.

## 3. Consequences

- Do **not** encode the whole corpus as one flat Klein-4 blob. The ordered fiber
  (G4, Klein-4 sectors) and the co-occurrence metric (B-DNA, Laplacian) are both
  present, read by region.
- This is the biology-native form *"the irrep information storage demands"* — the
  same shape at two folds, not two competing schemes.
- It keeps the vocabulary honest: no new privileged primitive class — G4 is a *fold*
  (a read/region), not a new operator.

## 4. Composes

F1228 (directed genome = metric + charge), ADR-0002 (one Laplacian, two reads),
`[[feedback_relational_not_dense_distributional_not_sparse]]` (relational vs
distributional), `[[feedback_no_privileged_primitive_classes]]` (G4 is a fold, not a
new class). srmech: `srmech.amsc.hdc.klein4_*`, `srmech.amsc.laplacian.magnetic_laplacian`.
