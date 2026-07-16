# ADR-0006: The lichen — a set of genomes co-expressed on demand (melange)

**Status:** Accepted.
**Date:** 2026-07-16.
**Authors:** Steven Kirkland + Claude Opus 4.8 (1M context).
**Supersedes:** none.
**Superseded-by:** none.

---

## 1. Context

The collapse target the user set for the whole storage redesign:

> *"our goal is to try to store and retrieve knowledge in the same manner as biology
> shows us how the universe does it. so we do need to collapse all into a genome or
> set of genomes that create our lichen like structure on simulated demand."*

This is the top-level shape ADR-0001…0005 build toward: not one monolithic store,
but a **biology-native lichen** of many organisms coupled only when a query needs
them.

## 2. Decision

Knowledge is a **SET of Class-L genomes** — each corpus / domain is its **own full
genome**, never merged into a global blob. At query time:

1. **Couple** two or more genomes via a **sparse bridge** `C` into the block form
   `[[L_A, C], [Cᵀ, L_B]]`.
2. **Co-express** (`gene_express` / EPH = responsion) — excite both at once.
3. **Harvest** the emergent **cross-genome modes** — modes invisible to either
   genome alone (the lichen's new metabolism).
4. **Discard the coupled op** — the bridge is a *per-query* read, never stored. The
   individual genomes (the towers) persist.

*"On simulated demand"* = the coupling is expressed only for the query that needs
it, then dissolved. Biology: **lichen / mitonuclear / syntrophy** (F1205) — separate
organisms whose joint metabolism exists only while coupled.

## 3. Consequences

- **(+)** Domains stay **separable and independently attestable**; a new corpus adds
  an organism without re-encoding the existing ones.
- **(+)** Cross-domain answers are a **demand-time read**, not a storage-time merge —
  no combinatorial pre-computation.
- **(−)** Cross-mode validity must be **guarded** — the homograph failure (a spurious
  cross-mode from a shared surface token) is the known trap (F768); melange
  validation is its own arc (#263).
- **(−)** The bridge `C` is per-query and must never be cached as if it were truth.

## 4. Composes

`[[project_genome_melange_coexpress_separate_class_l_genomes]]` (F1205 — lichen /
mitonuclear / syntrophy, sim + OA-cited),
`[[project_class_L_store_class_M_working_memory_reversible_spectral_bridge]]`
(L = store, the bridge = reversible basis-change), F768 (homograph guard), ADR-0001 /
ADR-0002. Arcs: #262 (ProofWiki as its own genome), #263 (melange validation).
