# ANDY Research Platform — Architecture v0.2

Decision agreed 2026-11-26. Supersedes the separate software directories for Signature and Factory proposed in ANDY_FACTORY_THREE_INSTANCE_ARCHITECTURE_v0.1.md; retains runtime isolation and controlled evidence transfer. Reference: ANDY_SIGNATURE_FOUNDATION_1.0_RC1.md.

## Single installation
One distributable GitHub repository, shared Engine, LLM Bridge, GPAI provider/model registry, Data Core implementation, UI components and tests. Separate processes: Signature 8082 (Arena, Replay, Lab, Data, Designer, Signature) and Factory 8083 (queue, budget, funding, production, model qualification). Studio 8080 remains independent for now. Keep current folder name during migration. Separate runtime roots, SQLite files, run directories, evidence, locks, sessions and role-specific write permissions. Shared model configuration must have controlled writes, versioning and atomic updates. Secrets remain local and excluded from distribution. No automatic paid calls. Factory production remains disabled until explicit release gates pass.

## Research cycle
Research question → Factory series → validated evidence → Signature analysis → versioned Behavior Model Card → new research question. Lab development remains story-driven; Journal can communicate validated findings. A new completed series may substantially change a Model Card. Statistical significance is a separate question, not implied by magnitude of change.

## Evidence and Model Cards
Completed eligible evidence is transferred via a controlled, idempotent, atomic import; retain originals and provenance, detect conflicts, exclude technical tests, avoid silent substitutions. A completed series may trigger recalculation after acceptance; no automatic inclusion of incomplete or incompatible cohorts. Preserve exact provider/API identity, requested and reported IDs, configuration, rule and metric versions, cohort membership, sample size, evidence revision and prior card states. Unknown is not zero. K4 nodes Decisions, Executed, Input Tokens, Output Tokens; six ratio edges. Distinguish pooled ratio-of-sums from equal-game aggregation. Compare like-for-like and report coverage/uncertainty. Versioned snapshots enable before/after series comparisons. Proposed automatic refresh is not yet implemented; design for explicit acceptance first.

## Implementation sequence
1. PLATFORM-01 / RUNTIME-01: inventory hardcoded paths and introduce role-specific runtime resolution, preserving current Signature behavior and RC1 rollback.
2. FACTORY-MERGE01: retain queue, budget, funding, UI and offline production safeguards. Do not overwrite existing Factory runtime data.
3. LAUNCH-01: independent and simultaneous launch profiles; no assumption that port alone isolates state.
4. GPAI-CORE01: shared model/provider configuration, historical identities immutable; new models via configuration where compatible, new protocol via adapter. MiMo candidate pilot, compatibility not yet verified.
5. PLATFORM-GATE01: offline parallel operation, data isolation, designer role checks, regression and portable installation; actual live Resume/Refund and production gates remain open.
6. SYNC-06: validated evidence transfer and model metadata provenance.
7. FACTORY-RUNNER01: explicitly authorized production.
8. SIGNATURE-01 / Behavior Model Cards: versioned empirical profiles and series impact analysis.
9. PUBLIC-RELEASE01: public distribution, secret exclusion, licensing and curated data release review.

Status: architecture decision documented; no source migration, automatic refresh, production activation or new release tag performed. RC1 is the verified local rollback snapshot. Existing Factory archive and Studio remain untouched.
