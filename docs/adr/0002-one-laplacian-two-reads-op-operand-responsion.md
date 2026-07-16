# ADR-0002: One Laplacian, two reads — op(x)operand(x)responsion (k=3)

**Status:** Accepted.
**Date:** 2026-07-16.
**Authors:** Steven Kirkland + Claude Opus 4.8 (1M context).
**Supersedes:** none.
**Superseded-by:** none.

---

## 1. Context

We had been describing the genome as *"an Abelian Laplacian **plus** a non-Abelian
other thing,"* which reads like **two** objects. The user corrected this:

> *"we only have one laplacian object that serves two purposes, can be read more
> than one way to extract the information in an ordered way … I thought there was a
> third that … again represented our op(x)operand(x)responsion shape … and that
> it's the responsion that is the non-commutative."*

And asked why the responsion carries `−iLz` under a Wick rotation.

## 2. Decision

There is **one** Class-L object with **k=3 read-outs** — the
`op(x)operand(x)responsion` shape:

| Read | What it yields | Character | Answers |
|------|----------------|-----------|---------|
| **edges** | the co-occurrence graph | RELATIONAL, Abelian | *"what it's like"* (neighbourhood) |
| **eigenvectors** | the spectral basis | DISTRIBUTIONAL | the coordinate frame |
| **eigenvalues / responsion** | the ordered walk | **non-Abelian, ordered** | *"what it IS"* (the definition/fiber) |

The **responsion** is the third read, and it is where order (non-commutativity)
lives. It is **not a second object** — it is a different *read* of the same
Laplacian.

**The responsion physics.** `responsion(L, u0, z, kind="propagator") = e^{−zL}·u0`.

- The **minus** sign is because `L` is **positive-semi-definite** — a relaxation /
  decay generator (heat flow), not `−iH`. `e^{−zL}` damps; it does not merely rotate.
- The **`i`** lives in `arg(z)`, not in a bolted-on `−i`. `z` **real** → thermal /
  relational read (the diffusive "what it's like"). `z = it` (a **Wick rotation** to
  the imaginary axis) → `e^{−zL} = e^{−iLt}` — the **coherent, ordered walk** ("what
  it IS"). That substitution is exactly where the `−iLz` the user asked about comes
  from: it is the *coherent case* of the one propagator, not a different formula.

So `z` is the **coherence dial** (F1075) at the physics layer: turn it real for the
relational edges read, turn it imaginary for the ordered responsion/fiber read. `i`
is a 90° rotation — a real direction, not "unreal" (F256 / dignity-first).

## 3. Consequences

- Never build two separate objects. The relational read and the ordered-definition
  read come from **one genome** by choosing `z`.
- *"Non-Abelian Laplacian"* is a legitimate name for the responsion read — but it is
  the **same** `L`, read coherently.
- Siona's reply pattern falls straight out: **lead with the responsion read** (the
  definition) then the **edges read** (the relations) — see ADR-0007.

## 4. Composes

F1075 (the coherence dial), F256 (`i` = 90°, a real direction — dignity-first),
F1132 (relational vs distributional), F1146 (bit-exact = phase-locked cyclic slots),
`[[stance_bit_exact_is_phase_locked_cyclic_slots_not_flat]]`, the
`op(x)operand(x)EC` triality (`[[project_op_x_operand_x_ec_triality_and_srmech_genome_overhaul]]`).
srmech: `srmech.amsc.laplacian.responsion`.
