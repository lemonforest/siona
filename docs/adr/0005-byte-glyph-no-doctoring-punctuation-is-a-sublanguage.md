# ADR-0005: Byte/glyph, no doctoring — punctuation is a sublanguage

**Status:** Accepted.
**Date:** 2026-07-16.
**Authors:** Steven Kirkland + Claude Opus 4.8 (1M context).
**Supersedes:** none.
**Superseded-by:** none.

---

## 1. Context

The earlier full-body encode **stripped punctuation** before encoding, so the
recovered definition read run-on ("… clear has no taste or smell and is almost").
The user rejected the strip outright:

> *"why would encode strip punctuation? that is sentence structure. I don't think
> that's correct. we aren't supposed to strip anything, we use sublanguages to
> understand, not doctor the text."*

Stripping is **doctoring the SSoT**. A strip does not simplify — it *hides a missing
kernel*: the honest response to markup/punctuation you can't yet parse is to surface
the gap and build the kernel, never to delete the bytes (F764 / F817).

## 2. Decision

- **Tokenize keeping punctuation as its own tokens**
  (`re.findall(r"\w+|[^\w\s]", text)`). Punctuation is a **sublanguage to
  comprehend**, never stripped. Markup is likewise a *form layer* to understand via
  a kernel, not to pre-clean away.
- Each token's **bytes are the ni-Vanuatu order-native byte/glyph base** — the
  abstract translation base every language kernel builds *from*
  (`[[project_ni_vanuatu_byteglyph_is_the_order_native_base_of_all_kernels]]`).
- **Coherency = the same operations at different fractal-tower perspectives**
  (byte ↔ glyph ↔ token ↔ document). The encode is **byte-exact**: what goes in
  round-trips out, punctuation included (proven in the ADR-0001 atom).

## 3. Consequences

- **(+)** Sentence structure survives the encode; the definitional read is a clean
  sentence, not a run-on.
- **(+)** No missing kernel is ever masked by a silent strip — a gap becomes a
  visible "build this sublanguage kernel" task.
- **(−)** Larger vocabulary (punctuation and markup tokens are first-class); the
  corpus re-encode (PKG-3) must be punctuation-preserving from the start.

## 4. Composes

`[[feedback_no_doctoring_ssot_use_sublanguage_kernels]]` (F764 / F817),
`[[project_ni_vanuatu_byteglyph_is_the_order_native_base_of_all_kernels]]`,
ADR-0001 (genome-native store), the byte/glyph fractal-tower coherency framing
(F1079 / F1080 winding tower).
