# Siona — Architecture Decision Records (ADR)

This directory holds the Architecture Decision Records for **Siona**, the RBS-HDC
natural-language instrument built on `srmech` (Stored-Relationship Mechanism) as
its lean math core. Format follows the srmech-family `ADR-NNNN` convention: **one
file per decision, small and scoped, never monolithic** (mirroring the way the
parent monorepo scopes `docs/adr/`).

Each ADR captures **one** decision as **Status / Context / Decision /
Consequences**, and forward-links the research findings (`FXXXX`) and proof
scripts it rests on — the *breadcrumb-web* discipline, so a decision survives
even when the notes are not in context.

This first tranche (0001–0008) captures the **genome-native storage** design
worked out over the 2026-07 conversation — the collapse of Siona's knowledge
into a biology-native lichen of genomes — recorded **before** the full corpus
encode (PKG-3) begins.

---

## Index

| ID | Title | Status | Date |
|----|-------|--------|------|
| [ADR-0001](0001-knowledge-is-genome-native-not-plaintext.md) | Knowledge is genome-native, not plaintext | ✅ Accepted | 2026-07-16 |
| [ADR-0002](0002-one-laplacian-two-reads-op-operand-responsion.md) | One Laplacian, two reads — op(x)operand(x)responsion (k=3) | ✅ Accepted | 2026-07-16 |
| [ADR-0003](0003-no-plaintext-toc-content-addressed-index.md) | No plaintext table of contents — the index is content-addressed | ✅ Accepted | 2026-07-16 |
| [ADR-0004](0004-dna-plus-g4-dna-region-dependent-encoding.md) | DNA + G4 DNA — region-dependent encoding (Laplacian backbone + Klein-4 chirality) | ✅ Accepted | 2026-07-16 |
| [ADR-0005](0005-byte-glyph-no-doctoring-punctuation-is-a-sublanguage.md) | Byte/glyph, no doctoring — punctuation is a sublanguage | ✅ Accepted | 2026-07-16 |
| [ADR-0006](0006-the-lichen-set-of-genomes-coexpressed-on-demand.md) | The lichen — a set of genomes co-expressed on demand (melange) | ✅ Accepted | 2026-07-16 |
| [ADR-0007](0007-output-is-sentences-attested-and-cited.md) | Output is sentences, attested and cited | ✅ Accepted | 2026-07-16 |
| [ADR-0008](0008-grounded-intent-over-positional-router.md) | Grounded-intent over positional router | 🔄 Proposed | 2026-07-16 |

**Status legend:** ✅ Accepted · 🔄 Proposed · ⏳ Draft · 🗑 Superseded.

## Scope note

These are **algebra / eigenbasis / cyclic-group / spectral side** decisions (the
framework-research discipline). They do **not** cover CAD / fabrication /
mechanical geometry — out of scope per the CAD-grade ban carried from the parent
monorepo.
