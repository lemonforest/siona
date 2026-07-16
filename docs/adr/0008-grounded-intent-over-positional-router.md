# ADR-0008: Grounded-intent over positional router

**Status:** Proposed (the standing next step; not yet built).
**Date:** 2026-07-16.
**Authors:** Steven Kirkland + Claude Opus 4.8 (1M context).
**Supersedes:** none.
**Superseded-by:** none.

---

## 1. Context

The current `route` recognises intent frames by **position** — it matched the
`define` frame only utterance-**initial**, so *"in detail, what is water?"* fell
through to the substrate branch and returned *"(no substrate content yet)"* until a
band-aid stripped leading verbosity operators before matching. Each such fix is a
hand-coded positional patch. The user asked the load-bearing question twice:

> *"why does it need a router to understand intent when we have a knowledge and
> language kernel that describes it?"*

Every accreting per-frame fix is evidence that a **positional** router is the wrong
shape.

## 2. Decision (proposed)

Replace the positional router with **knowledge + language-kernel-grounded intent**:

- The **language board already declares the operators** (operators are declared by
  rule — `[[feedback_operators_declared_operands_by_meaning]]` / F770). Verbosity
  markers ("in detail,", "briefly,") are *operators*, recognised as such, not
  positional noise to strip.
- The **knowledge kernel already describes each intent** (`define` = *"Define a
  concept…"*). Intent should be recognised by **grounding the utterance against
  those declared operators + described intents**, not by token position.
- Discipline: **operators declared, operands derived by meaning** — do not derive
  operators from meaning, and do not encode intent as a positional stoplist.

## 3. Status note

The user chose *"both, definition first."* The **definition read is done** (ADR-0001
/ ADR-0002, F1241). The **grounded-intent refactor is the deferred half** — recorded
here so the direction is not re-litigated and the positional band-aids are known to
be interim.

## 4. Consequences (expected)

- **(+)** Removes the accreting per-frame positional patches (F1240's "in detail" fix
  is the worked example of the debt).
- **(+)** Intent generalises to unseen phrasings without new positional code.
- **(−)** Requires the language board + knowledge kernel to expose intent
  descriptions in a form the grounder can match against (design work, not yet done).

## 5. Composes

F1240 / F1241 (the routing miss + the definition read),
`[[feedback_operators_declared_operands_by_meaning]]` (F770),
`[[feedback_correct_user_wrong_words_against_record]]` (F767 — operation-verb
discipline), F1010. Supersession: when built, this ADR moves to **Accepted** and the
positional-router notes in the code are removed.
