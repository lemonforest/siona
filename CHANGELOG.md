# Changelog — siona

All notable changes to the `siona` package. Versioning: `X.Y.ZrcN` tags publish to **TestPyPI**;
clean `X.Y.Z` tags to **PyPI** (the human production gate). Each rcN ships via its **own PR**.

## 0.1.0rc1 — the UN-MIRROR cut (in progress; unreleased)

**Breaking / identity:** `siona` stops being a co-name alias for `srmech` (releases ≤ 0.0.4 were a
metadata-only mirror; srmech rc173 removed the in-wheel `import siona` alias) and becomes its **own
package**: the grounded inference layer, a **srmech profile plugin** (`srmech.profiles` entry-point)
on a lean `srmech>=0.8.1` dependency. The **wheel** stays lean — no corpora bundled inside it;
instruments and knowledge load by path. Knowledge **kernels are distributed as attested companion
artifacts** (CC-BY-SA-compliant by the MPR attestation each acquired fact carries — see
`PKG1_DECISION.md`).

### Added
- `siona.bridge` — the de Bruijn fiber walk + full-body recall (walk/recall/route/two_mode_recall);
  symbol-agnostic (integer ids); pure-Python, exact.
- `siona.infer` — the grounded inference loop (research findings F1008–F1012):
  - `Session.route` (F1010): intent routing {define | tool-call | self-command | continue} by
    **declared operator frames + operand shape** — no similarity thresholds (that signal was
    measured and rejected as non-separable).
  - `Grounding` (F1008): utterance→tool grounding over srmech's **live** `tool_schema` registry
    (name-weighted, order-carrying unigram+adjacency-bigram encoding; 347-tool surface).
  - `Session._drive_tool` (F1009): signature-fit on typed parameters → resolve → **run the real
    srmech op** → read the result into working memory; (F1012) cross-turn operand resolution —
    a turn may reference a value **remembered in an earlier turn**.
  - the self surface (F1011): siona's own 8 tools registered into srmech's registry via
    `register_profile_tools` — one registry, two surfaces; `help` answers from the **live** schema
    (Class-H self-introspection).
  - ingested knowledge **kernels** (F1012): declared linear-map form; composition is
    **exact-rational** (integer num/den, srmech `cyclic.gcd` reduction, collapse only at display).
- `siona.boards` — the language-BOARD layer (PKG-1): per-language **declared operator profiles**
  (`Board`, `ENGLISH`, `load_board` TOML descriptors) on the byte/glyph substrate (script-agnostic;
  anagram-distinct). **English is board #1, not the architecture.** Rosetta-layer lineage (F649,
  ni-Vanuatu as living exemplar) documented dignity-first — exemplar + pointer, never data.

### Added — the natural-language instrument (describe / translate; research F1118–F1166)
- `siona.couple` — the **pipeline-collapse**: ONE signed Class-L coupling operation whose *residue* IS the
  read-outs (spine = key concepts, communities = aspect groups, coherence, render order). Built on
  `srmech.amsc.laplacian` (`signed_laplacian` + `symmetric_eigendecompose`), numpy-free. The case-role enters
  as a ±1 **chirality sign** (not a tuned weight), so the partition falls out for free. **Dataset-agnostic** —
  the same residue-read recovers structure from *any* relational dataset (glyphs, English co-incidence, or a
  purely abstract cluster graph), because it is pure spectral structure.
- `siona.analytic` — **analytic / isolating** languages (English, Mandarin, Vietnamese …): sparse relational
  knowledge → structured describe. Selection = `couple()`'s residue on a co-incidence (`relate`) graph;
  aboutness-gated. English (simplewiki relate) is the first instance.
- `siona.anchor` — the cross-lingual **glyph→concept anchor** (the FORM axis for logographic / non-cognate
  scripts): Egyptian Vygus + Sumerian ETCSL lexicons; lemmatization; sense-disambiguation. Plus the
  **synthetic / agglutinative** morphology read: `determinative` (semantic-class classifier), `case` (operand
  relational role), `verb_infixes` / `verb_direction`, `coupling_ec` (the case↔infix redundancy = op(x)operand
  **EC**), and `render_cased` (case-driven render).
- `siona.sumerian` — the Sumerian **sub-language kernel** (markup → class dispatch): the determinative as the
  coherency-agnostic type tag; the genome surface `(concept, class)` per glyph.
- `siona.g4` — **selective, automatic chirality-stabilization** (the G-quadruplex analog): the metamer is the
  motif; the full-chirality Klein-4 fold fires only where flat collapse is lossy (~4% of loci), flat elsewhere.
- `siona.translate` / `siona.sense` / `siona.chirality` / `siona.relate` / `siona.conceptnet` / `siona.graft`
  — the relational meaning stack: cross-substrate MNN-invariant translation; the three type-independent axes
  (form / relational / chirality); antonym-opponent chirality; co-incidence + typed-relation neighborhoods.

### Discipline
- Bag-of-words audit **clean** (PKG1_DECISION §audit): every content encoding carries order; an
  order-free bundle may only be a weighting statistic. Regression set: F1004/F1008/F1010.
- **srmech-first, numpy-free** across the NL stack — every spectral op is `srmech.amsc.laplacian.*`; no `abs()`
  (Class-K magnitude); no tuned magic weights (couple() carries the role as a structural ±1 sign, attested).
- Publish gate: see `PUBLISH_GATE.md` (publisher-repo move, notebook stays with mlehaptics RTD,
  hardening backlog before the rc1 tag).

## 0.0.4 and earlier (historical)
- Metadata-only co-name alias for `srmech` (retired; see the un-mirror note above).
