# ADR-0003: No plaintext table of contents — the index is content-addressed

**Status:** Accepted.
**Date:** 2026-07-16.
**Authors:** Steven Kirkland + Claude Opus 4.8 (1M context).
**Supersedes:** none.
**Superseded-by:** none.

---

## 1. Context

The plaintext store shipped a separate `_index.json` — a **plaintext table of
contents** of 240,823 titles — as the lookup path into the bodies. The user:

> *"a genome should not have a table of contents or index in plain text. Such a
> thing can be created for human readability, but it should all come from the genome
> encoded op(x)operand(x)responsion shape, all inside as DNA + G4 DNA as the irrep
> information storage demands."*

A plaintext index is a second source of truth sitting outside the genome — exactly
the kind of un-encoded artefact ADR-0001 removes.

## 2. Decision

The index is the **content-address** of each document. The genome label is
`sha256_bytes(title.encode())[:16]` (Class A — content-addressing, the foundational
op every cascade begins with). Lookup is *address → chromosome*; there is **no
plaintext index** as source of truth.

A human-readable table of contents **may be generated** for convenience, but it is
**derived, regenerable, and never authoritative** — it comes *out of* the genome
(the set of content-addresses + their byte/glyph vocabularies), never the other way
round.

## 3. Consequences

- **(+)** One store, no drift: there is no plaintext index to fall out of sync with
  the genome or to be silently doctored.
- **(+)** Lookup is a Class-A content-address — the same primitive the whole cascade
  vocabulary is anchored on.
- **(−)** `title → address` is one-way (sha256); a reverse *human* TOC (address →
  title) must be regenerated from the stored vocabularies. This is cheap and derived,
  not a stored index.

## 4. Composes

ADR-0001 (genome-native store), Class A content-addressing
(`srmech.amsc.format.sha256_bytes`), F1242 (the atom uses the title content-address
as the label), `[[feedback_no_doctoring_ssot_use_sublanguage_kernels]]`.
