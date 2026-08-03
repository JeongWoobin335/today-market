# today-market — Stage 1→5 Identity Pipeline Run

**The actual run output of the identity pipeline (stages 1→5): starting from a single input document — the Today Market API specification — it automatically derives the full chain from concept (Identity) to executable skill (Skill).**

This repository is the pipeline's **runRoot** (per-run working folder); every artifact here was produced through the five stages below. A skill is never a hand-written file — it is the **terminus of a chain**.

> **Built on [Common Context Structure (CCS)](https://github.com/gesia-platform/Common-Context-Structure)** — the standard vault grammar (folder structure, derivation-chain layout, and naming laws) this run instantiates — **and executed with [Identity-Pipeline-Skill](https://github.com/gesia-platform/Identity-Pipeline-Skill)** (`stage_1_to_5_identity_pipeline_skill`), the sealed composite skill that ran the whole 1→5 pipeline as one invocation. CCS provides the common frame, the skill provides the runner; this repository fills the frame with one concrete pipeline run over the Today Market API specification.

```
Identity ──definesGoal──▶ Goal ──requiresTask──▶ Task ──requiresKnowledge──▶ Knowledge ──appliedThrough──▶ Method ──developsSkill──▶ Skill
(concept)                 (goal)                 (task)                      (knowledge)                   (method)                   (skill)
```

---

## Pipeline Structure (Stages 1→5)

The pipeline is a loop-free composite: three sealed members fire serially, exactly once each. All repetition lives only inside the internal procedures of members 2 and 3.

```
[Input: _input document corpus + FROZEN _identity registry snapshot]
        │
        ▼
Member 1 ─ Diagnostic HEAD (S1 → S2 → S3 → 4-DIAG)
  S1  Candidate extraction    Extract identity candidates from the corpus; seal the C0 roster (KEEP+MANUAL)
  S2  Identity fragmentation  Split/merge adjudication along a single axis → the C1 output set
  S3  Knowledge-chain ordering Topological ordering over relation edges → the CandidateSetForStage4 roster
  4-DIAG Surface diagnosis    SIMULATION only (no closure minted); duplicate/containment/concept-thinning diagnosis
        │                       → Stage5HandoffPacket (admitted set + invocation order)
        ▼  E1 (optional diagnose-then-build gate: admitted set ⋉ Stage-3 roster)
Member 2 ─ candidate_sweep (per-candidate 4-EXEC loop, strict-serial, stop-on-failure)
  Mints each candidate's 6-file closure chain
  _identity → _goal → _task → _knowledge → _method → _skill,
  sealing each with its own per-candidate validation (PASS)
        │
        ▼  E2 (completed handoff: minted-PASS set in manifest order)
Member 3 ─ ledger_culmination (C1 ledger-append loop + completeness barrier + C2 once)
  Writes the feedback ledger → per-stage patch instructions → seals the next-run seed packet
        │
        ▼
[Terminal sink: Stage5NextRunSeedPacket + verified RUN record]
```

---

## This Run's Results (2026-08-03)

- **Input**: [`_input/_document/오늘마켓_API_명세서.md`](_input/_document/) — one document (Today Market API specification)
- **Frozen `_identity` snapshot**: empty registry (first run)
- **runID**: `stage1_20260803_todaymarket_purchase_api` (minted internally by S1)

| Stage | Result | Gate |
|---|---|---|
| S1 Candidate extraction | 15 candidates → KEEP 7 / MANUAL 3 / DROP 5; C0 roster 10 rows | PASS |
| S2 Identity fragmentation | C1 = 10 (KEEP 6 + SPLIT fragments 4), ManualReview 3 | PASS |
| S3 Knowledge-chain ordering | CandidateSetForStage4: 10 rows, topologically ordered | PASS |
| 4-DIAG Surface diagnosis | All 45 pairs swept; 9/10 admitted (`todaymarket_api_server` excluded as an over-broad parent) | PASS |
| Member 2 sweep (4-EXEC ×9) | 9/9 minted-PASS — 54 closure files + 9 validation artifacts | PASS |
| Member 3 ledger culmination | 9 ledger entries, barrier HELD, C2 exactly once — **no-change seed** (all 4 stages NO_FEEDBACK_NEEDED) | PASS |

### The 9 Derived Identities (in invocation order)

1. `PRODUCT` — product
2. `PURCHASE_REQUEST` — purchase request
3. `ERROR_RESPONSE` — error response
4. `ROOT_PAGE_ENDPOINT` — web page serving endpoint
5. `PRODUCT_LIST_ENDPOINT` — product list retrieval endpoint
6. `AMOUNT_VALIDATION` — amount validation
7. `PURCHASE_ENDPOINT` — product purchase processing endpoint
8. `PURCHASE_RECORD` — purchase record
9. `PURCHASE_HISTORY_ENDPOINT` — purchase history retrieval endpoint

Each identity completed its 6-file closure chain from `_identity/<NAME>.md` through `_skill/<NAME>/SKILL.md`.
(`todaymarket_api_server` was excluded from skillization — it risked silently absorbing its four endpoint children — and was recorded as boundary re-scoping feedback instead.)

---

## Folder Structure

```
today-market\  (= runRoot)
│
│  ◆ Chain entry
├── _input\
│   └── _document\    The document corpus the pipeline consumes       오늘마켓_API_명세서.md
│
│  ◆ Derivation chain (one file per concept in each folder)
├── _identity\        Concept definitions — the root of everything.   <UPPERCASE_CONCEPT>.md
├── _goal\            Chain stage 1: goal                             <concept>_goal.md
├── _task\            Chain stage 2: task                             <concept>_task.md
├── _knowledge\       Chain stage 3: knowledge (criteria)             <concept>_knowledge.md
├── _method\          Chain stage 4: method (procedure)               <concept>_method.md
├── _skill\           Chain terminus: skills                          <NAME>\SKILL.md
│
│  ◆ Run outputs (artifacts sealed by the pipeline)
├── _artifact\
│   ├── <stamp>_stage1_..._artifact.md            S1 sealed artifact (C0 roster)
│   ├── <stamp>_stage2_..._artifact.md            S2 sealed artifact (C1)
│   ├── <stamp>_stage3_..._artifact.md            S3 sealed artifact (Stage-4 roster)
│   ├── <stamp>_stage4_diag_*.md                  The 6 4-DIAG diagnosis artifacts
│   ├── stage4_<n>_<name>_..._artifact.md         Per-candidate 4-EXEC closure validation (×9)
│   ├── stage4_concept_to_skill_closure_manifest.md   Sweep manifest (accumulator)
│   ├── stage5_<n>_<name>_..._artifact.md         Per-candidate feedback records (×9)
│   ├── stage5_feedback_ledger.md                 Feedback ledger
│   ├── stage5_stage{1..4}_patch_instruction.md   Per-stage patch instructions (this run: all explicitly empty)
│   ├── stage5_next_run_seed_packet.md            Next-run seed packet (NOT consumed)
│   └── stage5_run_record.md                      Verified RUN record
│
│  ◆ Reserved structure (machinery seats — empty in this run)
├── _entity\          Composite authoring audit trail (9 stages: suite→…→composite)
└── _deploy\          Deployment staging (6 stages: closure→…→record)
```

---

## Design Principles

1. **No folder exists without a concept** — every artifact traces back to a concept definition in `_identity`.
2. **A skill is the terminus of a chain** — a skill is generated only after Identity→Goal→Task→Knowledge→Method has been built forward.
3. **A composite is not a loop** — the pipeline body is a single serial pass over 3 members and 2 edges; all repetition lives inside the members' own procedures.
4. **Finalize-then-read** — each member reads only its predecessor's PASS-gate-sealed artifacts, located by section heading.
5. **Any failure stops the whole run** — if any member fails its own gate, no later edge fires and the entire run STOPs.
6. **The seed is never consumed** — applying the next-run seed packet belongs to the NEXT run's pre-step; no return edge exists inside this run.
7. **Every link is verified** — chain, roster, and artifact links are kept at zero dangling.

## Naming Laws

- Leading `_` = **folder marker** — never used in a file name
- Identity files are `_identity/<UPPERCASE>.md`; chain files are `<concept>_<stage>.md`
- Skills live at `_skill/<NAME>/SKILL.md`
- Run artifacts are named `<YYYYMMDD_HHMMSS>_<stage>_..._artifact.md` (stamp = run time)

---

> This repository is the result of ONE invocation of the [**stage_1_to_5_identity_pipeline**](https://github.com/gesia-platform/Identity-Pipeline-Skill) composite over the [Common Context Structure (CCS)](https://github.com/gesia-platform/Common-Context-Structure) vault grammar. The next run starts by reading the seed packet (`_artifact/stage5_next_run_seed_packet.md`) — this run's seed is an evidence-based no-change seed (NO_FEEDBACK_NEEDED ×4), so the pipeline can be rerun unchanged or ended here.
