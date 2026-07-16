# ADR-0001: Knowledge is genome-native, not plaintext

**Status:** Accepted.
**Date:** 2026-07-16.
**Authors:** Steven Kirkland + Claude Opus 4.8 (1M context).
**Supersedes:** none.
**Superseded-by:** none.

---

## 1. Context

Siona's knowledge was stored as a **plaintext NDJSON full-body instrument**
(`simplewiki_fullbody_instrument.ndjson`, 384 MB) plus a separate directed
co-occurrence genome. The definitional read (`body_lead`) recovered text by
reading the plaintext `s` field back through `bridge.recall`, which reported
`native: False` — the de Bruijn walk merely *verified* a plaintext payload
rather than *being* the store.

The user's challenge was direct: *"what is this full text ndjson dependency? why
doesn't this come from our laplacian + non-abelian fiber? I don't understand how
an ndjson file of text counts as encoded."*

A file of plaintext is not encoded. It is the raw source. An **encoded** store is
the genome shape — `op(x)operand(x)responsion` — from which text is a *render out*,
never the thing stored.

## 2. Decision

Every document is stored as a **genome-native Klein-4 (G4) DNA fiber**: the
ordered token-ids packed with `genome.kernel_pack(..., element_type="klein4")`,
content-addressed, byte-exact on round-trip. The genome **is** the store. Plaintext
(when a human needs it) is a walk-read *out of* the genome — it is never the source
of truth and is never kept as a parallel NDJSON.

This collapses two artefacts (the co-occurrence genome **and** the plaintext
full-body NDJSON) into **one organism per document**.

## 3. Proof

`R-RBS-LM-FIBERGENOME` — the atom (committed `138262fb` in the research subtree):
26 tokens → 78 Klein-4 fiber-symbols, content-addressed, **byte-exact** round-trip,
punctuation intact. The shape is proven; the corpus-scale encode is the follow-on
work (PKG-3 / #231).

## 4. Consequences

- **(+)** The store *is* the encoding — there is no plaintext shadow copy to drift
  from or doctor.
- **(+)** One document = one content-addressed genome; a *set* of them is the lichen
  (ADR-0006).
- **(−)** An encode pass over the whole corpus is required (PKG-3, ~240k bodies).
- **(−)** The id→token byte/glyph vocabulary must travel with, or be derivable from,
  the genome (see ADR-0003 / ADR-0005).

## 5. Composes

F1241 (definitions were already encoded — we weren't reading the store), F1242
(the fiber atom), the `op(x)operand(x)responsion` shape (ADR-0002),
`[[feedback_persist_genome_native_not_loose_json]]` (loose JSON is the regression),
`[[feedback_no_doctoring_ssot_use_sublanguage_kernels]]`. Arc: PKG-3 / #231.
