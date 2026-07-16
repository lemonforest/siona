# ADR-0007: Output is sentences, attested and cited

**Status:** Accepted.
**Date:** 2026-07-16.
**Authors:** Steven Kirkland + Claude Opus 4.8 (1M context).
**Supersedes:** none.
**Superseded-by:** none.

---

## 1. Context

An earlier output form emitted raw arrows:

```
water  -- etak ride -> water -> sq -> mi -> population -> census -> lived -> seat …
near: <- area, -> sq, <- mi, <- land, -> polo
```

The user rejected it:

> *"this is the incorrect form of siona output. everything needs to be sentences.
> we've worked this out already. we also showed the attested kernel, so needs
> attested genome now."*

## 2. Decision

- **Sentences, not arrows.** Siona renders natural-language **sentences** via the
  analytic render (`analytic.describe_from`), never raw edge dumps. The render layer
  (analytic / synthetic split by morphological typology; the vanuatu / sandroing
  language board) sits *on top of* the genome reads.
- **Definition first, then relations.** A reply **leads with the definition** — the
  responsion / ordered-walk read ("what it IS", ADR-0002) — then gives the relations
  — the edges read ("what it's like"). Turn context shapes verbosity (terse vs
  detailed); global context is not blindly turned verbose.
- **Attested and cited.** The corpus genome carries a mandatory **AMSC / MPR
  attestation** block, and **every reply is cited** to it (e.g.
  *"Simple English Wikipedia, CC BY-SA 4.0"*). **No-magic-numbers = attestation:** an
  un-attested store, or a hand-typed English reply, is a *magic number* — unreal
  until traceable to source.

## 3. Consequences

- The genome **must ship provenance** (source, license, retrieval, hashes) so the
  citation is real, not decorative.
- Replies are **composed from declared operands + inference**, not hand-authored —
  a bit-exact hand-typed string would be an unattested magic number
  (`[[feedback_hand_authored_replies_are_magic_numbers]]`).
- The render is the *last* layer: it reads the genome (ADR-0002), it does not store
  or doctor it (ADR-0005).

## 4. Composes

F1239 (the sentence render), F1241 (definition-first read), the AMSC / MPR discipline
(no-magic-numbers = attestation-to-source),
`[[feedback_hand_authored_replies_are_magic_numbers]]`,
`[[project_siona_analytic_vs_synthetic_typology_split]]`, ADR-0002. srmech:
`srmech.amsc.format` (MPR), `srmech.amsc.tool_schema` (attested catalogs).
