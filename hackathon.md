# Municipal Bureaucracy Path Visualizer — 36-hour implementation plan

Revised 26 September 2026 for Razeen Saiyed, Dhruv Shah, Soham Shirke, and Sahil Patil, incorporating the NSWS Know Your Approvals comparison.

This is a proposed implementation plan, not a record of implemented features. It is based on PSWB02 in the revised `PS  Internal Hackathon 2026.pdf` (page 3), all four supplied resumes, and inspection of the private repository's `main` branch at commit `07af85ae9f2e46436545aeb321d0c79f58dd452f`. The user confirmed approximately 36 hours and no currently specified special restrictions. Plan on using the existing template and external AI services; reconcile with the organizers' final rules if they change. Exact civic procedures and the AI provider remain to be selected.

## 1. Scope and requirements

Product goal: turn official civic requirements into a personalized, evidence-backed roadmap showing prerequisites, parallel steps, blockers, and what the user can do next. The user can declare documents or prerequisites already available, inspect why a dependency exists, and follow links to the official application service.

Target one jurisdiction, proposed Mumbai, and two fully sourced workflows, including at least one meaningful conditional branch. A third workflow is a stretch goal. Select workflows during the first two hours using both evidence completeness and comparison with existing official guidance. A workflow must include enough prerequisites to be usable, or explicitly display unresolved prerequisites and limited coverage.

### What NSWS changes

NSWS already offers approval discovery through a questionnaire. Its wider platform provides approval details, document requirements, applications and status tracking. These are overlapping capabilities, not novelty claims for this prototype. Its Maharashtra directory includes Building Plan Approval, so do not assume municipal requirements are absent. Sources: [NSWS FAQs](https://www.nsws.gov.in/faqs), [Maharashtra approvals](https://www.nsws.gov.in/portal/maharashtra).

The [official KYA guide](https://www.nsws.gov.in/s3fs/2022-11/How%20to%20operate%20KYA%20%28Know%20Your%20Approvals%29%20module%20on%20NSWS.pdf) describes questionnaires and consolidated approval lists, but is dated November 2022. The live questionnaire did not advance during the previous review. Consequently, the absence of a current dependency graph or equivalent functionality has NOT been established. A chatbot widget, BharatAssist, was also visible. Do not claim that adding chat, a graph database, or a checklist alone makes the product unique.

The proposed contribution is the quality of the dependency planning experience: explain the source for each relationship, expose verified parallel paths, identify blockers, and adapt preparation steps to declared existing requirements. Benchmark these behaviors before claiming an advantage. Retain the teachers' municipal PS; do not turn the prototype into a nationwide business approval portal.

NSWS becomes an official discovery/evidence source alongside the relevant municipal and departmental sources. It is not assumed to provide a downloadable dataset, public API, complete municipal coverage, or an integration agreement. Use publicly accessible material and direct links. NSWS itself advises checking relevant government portals for other approvals: [About NSWS](https://www.nsws.gov.in/about-us).

### First-two-hour workflow selection checkpoint

For each candidate, record its exact jurisdiction and applicant scenario, official URLs, source-backed steps and dependencies, unresolved facts, and what NSWS already exposes. Compare approval discovery, prerequisite explanation, ordering, parallel steps, declared existing documents, and next-action guidance. Label observations as verified, not observed, or inaccessible; inaccessible is not evidence of absence.

Select a workflow only when the team can demonstrate an evidence-backed path and a useful planning interaction. Require at least one documented conditional branch across the two workflows; show parallel execution only when the sourced process supports it. If a candidate is too incomplete or only reproduces an approval list, replace that candidate. Do not invent an elaborate graph to manufacture differentiation. Keep the two-workflow scope even if a third looks attractive.

### Requirements explicitly present in PSWB02

| ID | Requirement | Completion condition |
|---|---|---|
| R01 | Web-based civic task navigator | A user can navigate the complete flow in a browser. |
| R02 | Natural-language task input | Interpret multiple phrasings of supported tasks; do not require an exact service title. |
| R03 | Location and service context | Collect relevant location and service type; do not silently reuse another jurisdiction's rules. |
| R04 | Aggregate official government information | Demonstrate retrieval from selected official pages/documents and preserve their source identity. Use precomputation for the MVP; the brief does not specify fetching on every query. |
| R05 | Extract process information | Capture forms, documents, departments, offices, eligibility, fees, prerequisites, and application links where published. Unknown fields remain unknown. |
| R06 | Identify dependencies | Represent prerequisites and ordering explicitly, including steps that can occur independently. |
| R07 | Interactive visual roadmap | Show what to do, in what order, and where; a user can inspect individual steps. |
| R08 | Official source for every step | Each presented official step links to a relevant supporting official source. A generic portal homepage is insufficient if it does not support the claim. |
| R09 | Completion and progress tracking | Mark tasks complete, show overall progress, and clearly distinguish a user's checklist from government approval status. |

The brief also mentions an admin dashboard for review, validation, and updates, but explicitly makes it optional. The brief does not mandate a graph database product, embeddings, a vector database, live search on every request, all-India coverage, or application submission.

### Requirements proposed for our implementation

| ID | Requirement | Priority and acceptance |
|---|---|---|
| R10 | Clarifying questions | Core: ask for missing details that change the applicable path; avoid guessing eligibility. |
| R11 | Structured knowledge graph | Core: reusable procedures, steps, documents, offices, departments, jurisdictions, and typed relationships. URLs plus summaries alone do not satisfy this design. |
| R12 | Conditions and alternatives | Core: distinguish all-required and any-one-required groups; support a small explicit set of conditions. Unresolved conditions stay visible. |
| R13 | Evidence and provenance | Core: link claims and dependency rules to source versions and excerpts/page numbers, with source type and review status. Keep fetched time separate from reviewed time and published/effective dates. |
| R14 | Graph-first retrieval | Core: derive the applicable roadmap from reviewed data; retrieve linked passages for explanations. A separate vector RAG pipeline is unnecessary for the initial scope. |
| R15 | Source trust distinctions | Core: official requirements, third-party explanations, and community experiences are visibly different. Third-party or community material must not silently become an official requirement. |
| R16 | Review before publication | Core: extraction produces drafts; approve/correct before publishing. A reviewed seed/import is sufficient initially; a dashboard is a stretch feature. |
| R17 | Saved personal roadmaps | Core: save context and completion per Clerk user. Refreshing or signing back in restores progress. Users cannot access another user's roadmap. |
| R18 | Version-aware progress | Core: save the procedure version used by a roadmap. Publishing new rules must not silently change saved steps or reinterpret their completion. |
| R19 | Honest failure states | Core: unsupported task, ambiguous request, missing evidence, conflicting sources, stale information, and failed extraction have explicit responses. Do not generate a plausible-looking complete roadmap from missing evidence. |
| R20 | Useful step details | Core: requirements, applicability, office/portal, fee information if published, supporting excerpt, and source link. List/checklist alternative for narrow screens. |
| R21 | Limited source refresh | Core: allow an operator to re-fetch selected sources and create a new draft version. Preserve the published version until review. |
| R22 | Targeted live discovery | Stretch: when coverage is missing, search/fetch a limited set of suitable sources. Show candidate information as unreviewed; do not silently merge it into verified knowledge. |
| R23 | Admin dashboard | Stretch: inspect extracted claims beside evidence; approve/reject and publish a version. Enforce reviewer permission on the server. |
| R24 | Operational reliability | Core: bounded fetches/model calls, timeouts, helpful errors, extraction status, deduplicated imports, and server-side credentials. Constrain fetch destinations and redirects to avoid arbitrary internal-network access. |
| R25 | Verification and demo | Core: reviewed expected roadmaps, dependency/condition checks, user-isolation and persistence checks, build/lint checks, and a deployed end-to-end demonstration. |
| R26 | Declared existing requirements | Core: let users declare relevant documents/prerequisites already available. Reuse that declaration across applicable steps without uploading identity documents or claiming authenticity verification. |
| R27 | Next actions and blockers | Core: compute ready steps, unmet prerequisite IDs, and unresolved information from published rules. Explain why a step is blocked and link that relationship to evidence. |
| R28 | Explainable parallel paths | Core: distinguish necessary order from independent preparation. Display concurrent opportunities only where supported; do not introduce arbitrary ordering from page order. |
| R29 | Fair existing-product comparison | Core: document what NSWS provides for the selected scenarios, what this prototype demonstrates, and what remains unverified. Avoid unsupported superiority claims. |

### Deliberately outside the 36-hour core

- All-India coverage or arbitrary municipal processes.
- Automatic government application submission, payments, or official application-status integration.
- Uploading citizens' identity documents; a checklist is enough for this project.
- Large-scale social-media crawling, multilingual support, reminders, real-time collaboration, or graph editing by citizens.
- Separate Neo4j/vector databases and a second Python backend without a concrete need.
- An LLM making final decisions about applicability or dependencies without encoded, sourced rules.

## 2. Verified current template

Repository: [SohamShirke473/hackathon](https://github.com/SohamShirke473/hackathon).

```text
package.json / package-lock.json       npm workspaces: api, web
.github/workflows/ci.yml               install, typecheck, lint, build
api/
  src/app.ts                          middleware and route mounting
  src/config/                         environment validation and logging
  src/common/                         auth, validation, errors, pagination
  src/db/                             Neon client, schema exports, TODO seed
  src/modules/health/                 liveness and database readiness
  src/modules/todos/                  routes/controller/service/repository/
                                      schema/validation
  drizzle/                            existing TODO migration
web/
  src/main.tsx                        Clerk, QueryClient, theme, router
  src/router.tsx                      protected TODO page, sign-in/sign-up
  src/routes/                         root layout and pages
  src/features/todos/                 API calls, schemas, query hooks
  src/lib/                            authenticated fetch and query client
  src/components/                     protected route, theme, UI button
```

Existing stack: React 19 with Vite, TypeScript, Tailwind 4, shadcn configuration, React Router, TanStack Query, Clerk; Express, Zod, Drizzle, Neon PostgreSQL; logging, rate limiting, CORS, and error middleware.

The repository contains a user-scoped TODO application. It does not yet contain civic knowledge tables, extraction/crawling, AI intent handling, graph rendering, civic roadmap APIs, reviewer authorization, or automated domain tests. Reuse its conventions and infrastructure. Do not repurpose the TODO table as the knowledge graph; its title/completed fields cannot model civic facts and relationships.

The inspected commit has a [successful GitHub CI run](https://github.com/SohamShirke473/hackathon/actions/runs/36096679782). This review did not install or run the app locally. CI success establishes the configured checks, not civic functionality or a tested deployment. The web `typecheck` script uses `tsc --noEmit` against a reference-only root config; make it explicitly check the referenced projects. The web build already uses `tsc -b`.

## 3. Proposed architecture

Keep the current React/Vite + Express + Neon/Drizzle stack. Use relational tables to represent the knowledge graph. PostgreSQL supports recursive queries, although ordinary SQL plus application traversal may be sufficient for two small workflows. Add React Flow for visualization; automatic layout is a separate responsibility that Sahil should configure. [PostgreSQL documentation](https://www.postgresql.org/docs/current/queries-with.html), [React Flow documentation](https://reactflow.dev/learn).

Two paths share the same versioned evidence:

```text
Selected official sources
  -> bounded HTML/text-PDF retrieval
  -> source version and extracted text
  -> structured draft facts and dependencies
  -> validation and human review
  -> published knowledge graph + linked evidence

Task + location + user answers + declared existing requirements
  -> intent matching / necessary clarification
  -> published graph lookup and rule evaluation
  -> applicable roadmap + ready actions + blockers + supporting passages
  -> interactive graph, step details, saved user progress
```

AI handles language interpretation, draft extraction, and evidence-grounded explanations. Deterministic application logic evaluates the conditions we support, orders dependencies, and calculates readiness and progress. Razeen owns this evaluator; Sahil's saved-roadmap API calls it after progress changes. Frontend components display the returned result rather than creating a second rules engine. Graph nodes and edges come from published data. Do not allow generated prose to introduce unrepresented mandatory steps.

Separate applicability (applicable/not applicable/unknown), readiness (ready/blocked/needs information), user-reported completion, and evidence review status. A checked box does not mean government approval or official verification. When a user reverses a prerequisite completion, recompute downstream readiness; retain any downstream self-reported completion with an inconsistency warning rather than silently deleting it. Only applicable actionable steps contribute to completion; alternative documents are not additional compulsory tasks. Unknown applicability makes coverage/progress provisional.

This is retrieval-augmented generation using graph facts and their evidence. Add semantic passage retrieval only if testing shows that direct evidence lookup misses useful material. A new vector pipeline is not on the critical path.

Longer ingestion runs should be separate from a citizen's request. For the initial scope, a controlled ingestion command or simple background runner with persisted status is adequate; a distributed queue is not required. On-demand discovery is a later extension.

### Proposed data model

Razeen owns final schema names and migrations. These are conceptual groups, not a finalized schema:

| Group | Records and relationships |
|---|---|
| Source evidence | Sources, source versions, text passages/excerpts, claims and claim-to-source evidence links. |
| Civic knowledge | Jurisdictions, procedures and versions, steps, documents, offices/departments, application/form links. |
| Dependency rules | Prerequisite relationships, requirement groups, AND/OR semantics, conditions, and supporting claim IDs. |
| Personal state | Roadmaps with Clerk owner, context and pinned procedure version; declared existing requirement IDs; per-step self-reported completion. |
| Operations | Ingestion status and review/publish history. |

Dependency direction must be unambiguous. Shared prerequisite entities should be reusable across procedures. Published prerequisites should not contain unexplained cycles. Do not require every relation in the overall knowledge graph to be acyclic: only the executable dependency projection needs valid ordering.

### Proposed module placement and owners

All new paths below are proposals; they do not yet exist.

| Location | Purpose | Primary owner |
|---|---|---|
| `api/src/modules/knowledge/` | Civic entities, versions, evidence, graph lookup, applicability/readiness/progress evaluator | Razeen |
| `api/src/modules/ingestion/` | Fetching, text extraction, draft generation, source refresh and ingestion status | Soham |
| `api/src/modules/assistant/` | Task interpretation, clarification, procedure matching and explanations | Soham |
| `api/src/modules/roadmaps/` | Save/retrieve roadmaps and owner-scoped step progress | Sahil |
| `api/src/modules/reviews/` | Optional reviewer API; reuse knowledge publication logic | Soham, with Razeen |
| `web/src/features/graph/` | Canvas, nodes, edges, layout, selection, blocker highlighting and parallel-path display | Sahil |
| `web/src/features/navigator/` | Task input, context, clarifications and API hooks | Dhruv |
| `web/src/features/roadmaps/` | Saved roadmap UI, step details, progress controls and evidence display | Dhruv |
| `web/src/features/admin/` | Optional source-review interface | Dhruv |

Keep routes/controllers/services/repositories/validation consistent with the TODO module. Sahil owns graph-internal interactions; Dhruv owns the surrounding page and step-detail panel, connected through agreed props/callbacks.

Shared-file owners: Razeen owns schema exports and migration generation; Soham owns API route registration, backend environment additions, dependency coordination and CI; Dhruv owns frontend routing/layout and styling. Module authors submit their registration requirements to the shared-file owner. Sahil owns deployment integration, with Soham as backup. Install dependencies from the workspace root and coordinate lockfile changes.

### Shared contract v0 for the initial implementation

Use the following as the proposed common contract, not three independently invented APIs. At kickoff, Razeen and Soham publish the agreed field definitions and JSON examples as `docs/CONTRACTS.md` plus shared fixtures in the repository. That file is not present merely because this plan mentions it. Once created, it is the source of truth. If it is unavailable, each teammate can build an isolated module behind an adapter using clearly synthetic fixtures; unresolved fields and civic rules must not be silently finalized. Agree on small examples and Zod validation rather than building an elaborate shared-package framework first.

| Contract | Producer -> consumer | Required information |
|---|---|---|
| Extracted draft | Soham -> Razeen | Source version, entities, claims, dependency candidates, exact evidence references, unresolved fields. |
| Intent result | Soham -> Dhruv / Razeen | Discriminated result: `needs_clarification`, `ready`, or `unsupported`; matched procedure/jurisdiction where known; collected context; explicit questions or reason. Ambiguity leads to clarification. |
| Roadmap result | Razeen -> Sahil / Dhruv | Procedure/version/jurisdiction IDs, stable nodes/edges, requirement groups and evidence; evaluated applicability/readiness, unmet requirement IDs, next action IDs, completion summary and warnings. |
| Saved roadmap | Sahil -> Dhruv / graph | Roadmap ID, context/version, step completion and derived progress. Owner comes from the authenticated session. |
| Evidence details | Razeen -> Dhruv | Source title/URL, excerpt/page, source type, jurisdiction, relevant dates and review status. |

Proposed HTTP boundary to settle at kickoff:

| Endpoint | Owner | Behavior |
|---|---|---|
| `POST /api/assistant/resolve` | Soham | Accept task text, jurisdiction, structured answers and declared requirement IDs. Return clarification/unsupported, or a preview from Razeen's evaluator. Do not let the LLM invent graph nodes. |
| `GET /api/knowledge/evidence/:id` | Razeen | Retrieve source/excerpt and review metadata supporting a published claim. |
| `POST /api/roadmaps` | Sahil | Save from validated procedure-version ID, context and declared requirement IDs. Derive owner from Clerk and compute the graph on the server; do not trust client-supplied nodes/rules. |
| `GET /api/roadmaps` and `GET /api/roadmaps/:id` | Sahil | List/get only the authenticated user's roadmaps. Return the pinned procedure version and evaluated state. |
| `PATCH /api/roadmaps/:id/progress` | Sahil | Update an allowed step's completion or declared requirement; validate IDs against the pinned workflow and recalculate using Razeen's evaluator. Return the updated projection. |

Ingestion initially runs through a controlled command with persisted status and a draft export/import. Its operator HTTP endpoints and an admin interface are optional. No unprotected public crawler or publish endpoint.

Graph component boundary: Sahil exports a view receiving the evaluated roadmap, selected step ID, and selection/completion callbacks. Dhruv owns data-fetching hooks, the enclosing page and evidence drawer. Nodes carry stable IDs and `evidenceIds`; dependency edges identify prerequisite -> dependent, requirement-group membership, and evidence supporting the dependency. Readiness and progress are server-derived. All three teammates use one shared fixture, which includes an AND dependency, an OR alternative, an unresolved condition, and a completion reversal. Synthetic fixtures are development data, never displayed as real government guidance.

Any provider or teammate module that is unavailable sits behind an explicit interface. Mark an adapter mocked until integrated and tested; never report a fixture-based flow as live extraction, official verification, or backend persistence.

## 4. Team allocation based on the resumes

| Member | Why this assignment fits | Core deliverables | First deliverable |
|---|---|---|---|
| Razeen | SQL/PostgreSQL policy work, data ingestion and validation, LuraRent document analysis, FastAPI document workflows | Schema/migrations; source provenance; published graph queries; shared applicability/readiness/progress evaluator; reviewed dataset and expected-answer checks | NSWS comparison with Soham, shared contract fixture, and one reviewed procedure response |
| Soham | SourceMind's scraped-page/PDF ingestion, background jobs, Postgres/pgvector and AI retrieval; CodeCook's Express/Zod backend | NSWS/department source discovery; controlled ingestion; structured extraction; intent/clarification; grounded explanation; backend integration and CI | NSWS comparison with Razeen, shared contract, and one official source converted into an evidence-linked draft |
| Sahil | System Design Visualizer directly uses React Flow, React/TypeScript, PostgreSQL and backend validation; prior hackathon experience | Graph renderer and layout; dependency/blocker visualization; roadmap/progress API calling the shared evaluator; deployment integration | Fixture-driven graph showing selection, unmet prerequisites and independent branches |
| Dhruv | React/Next.js UI, Clerk/Convex integrations, API handling, mapping interfaces and a 24-hour team prototype | Navigator; context/clarification and existing-requirement input; next-action and evidence panels; saved roadmaps; responsive states; comparison/demo narrative; optional review UI | Input -> fixture roadmap -> next action and dependency-evidence panel |

Source collection is shared: after choosing the two workflows, Razeen and Dhruv assemble one source packet; Soham and Sahil assemble the other. A packet includes official URLs, relevant excerpts, prerequisites, unresolved applicability, and the expected sequence. Razeen coordinates consistency; each packet is cross-reviewed by the other pair. This prevents data validation from becoming one person's isolated bottleneck.

Soham should not build the graph UI or own the entire database. Razeen should not spend all 36 hours manually entering data. Sahil's graph experience is a direct advantage. Dhruv can build against agreed fixtures while backend work proceeds.

## 5. Proposed 36-hour sequence

Hours are elapsed event time and include coordination and breaks. The final two hours remain a buffer; do not fill them with planned features.

| Hours | Team outcome | Razeen | Soham | Sahil | Dhruv |
|---|---|---|---|---|---|
| 0–2 | NSWS comparison recorded; two workflows selected; contracts fixed; template runs | With Soham, compare candidate scenarios; draft schema and shared fixture | Verify accessible sources and provider setup; publish contract with Razeen | Confirm graph payload, blocker interactions and deployment approach | Sketch next-action, existing-requirement and evidence flows |
| 2–8 | First end-to-end sourced dependency roadmap | Seed reviewed workflow; return evaluated readiness and evidence | Ingest one real source; basic task matching | Render graph fixture, then real response; highlight blockers; begin persistence | Build input, clarification, roadmap shell, next actions and evidence panel |
| 8–16 | Two source-backed workflows, personalization and saved progress | Add second workflow, conditions, alternatives and existing-requirement evaluation | Connect extraction to draft storage; clarify ambiguous inputs | Complete owner-scoped progress APIs using shared evaluator; deploy early | Connect existing requirements, saved roadmaps, progress and failure states |
| 16–24 | Core requirements complete | Cross-review extracted rules; test alternatives and unknown context | Grounded explanations, refresh path, timeouts/retries; optional live lookup only if core is stable | Fix graph/selection/layout issues and deployment integration | Responsive list view and polish; optional minimal review screen |
| 24–30 | Scope freeze and joint verification | Check every published rule and dependency against evidence | Fix integration failures and invalid model outputs | Test save/reload, user isolation, graph branches | Run end-to-end user scenarios and correct confusing UI |
| 30–34 | Reliable demo and final deployed build | Prepare sourced dependency explanation and comparison evidence | Prepare ingestion/AI explanation and cached-data fallback | Verify deployment and graph demonstration | Prepare honest NSWS comparison, pitch/screens and rehearsal |
| 34–36 | Buffer, handoff and submission | Joint final smoke check, known limitations and submission support | Joint final smoke check | Joint final smoke check | Joint final smoke check |

At hour 8, the first real workflow must be visible in the app. At hour 16, a user must be able to reload a saved roadmap. At hour 24, freeze scope. If a milestone slips, cut the third workflow, broad live discovery, semantic search, admin polish and export features before cutting official evidence or the core roadmap experience.

The source-review mechanism remains necessary even when the admin UI is cut: use a controlled reviewed import. Preserve a reproducible ingestion example so the project demonstrates aggregation/extraction as well as manually reviewed knowledge.

## 6. Verification and demonstration

Create a compact reviewed evaluation set covering these behaviors:

1. Two natural-language phrasings lead to the same supported procedure.
2. Missing jurisdiction or a decisive applicability fact produces a clarification.
3. A verified condition changes the applicable steps correctly.
4. An OR requirement is not shown as every alternative being mandatory.
5. A prerequisite chain is ordered correctly; invalid dependency cycles cannot be published.
6. Every official step and rule has relevant supporting evidence; unknown fees stay unknown.
7. A saved roadmap and its completion survive reload; another account cannot read or modify it.
8. A refresh creates a draft without silently changing a published or saved roadmap.
9. Unsupported tasks and failed model/source calls remain understandable and do not fabricate results.
10. Input, graph, step details and checklist work on the target demo laptop and a narrow viewport.
11. A declared existing document satisfies only the matching supported requirement; it is labelled user-reported, not verified.
12. Reversing prerequisite completion recalculates blockers and next actions without erasing downstream self-reported work.
13. Parallel branches are based on reviewed process evidence, not an assumption that all unconnected steps are independent.
14. The comparison with NSWS uses the same scenario and distinguishes observed functionality from untested claims.

Use focused automated tests for dependency logic, ownership checks and extraction validation, plus browser checks for the end-to-end flow. Existing CI has typecheck/lint/build, not these domain tests. Add a test command for the meaningful new tests. During implementation, verify that each changed file compiles/typechecks before proceeding to the next file; run integrated checks after each completed feature.

Demo sequence: briefly acknowledge what NSWS already provides -> describe the selected civic task -> answer one decisive clarification -> declare an existing requirement -> show the remaining sourced dependency graph -> inspect why a step is blocked and what can happen next/in parallel -> mark a step done and observe the next-action update -> reload saved progress -> show one real extraction draft with its official source -> show an unsupported or unresolved case honestly. Keep a reviewed stored dataset available if live source fetching fails; label stored data and avoid presenting replayed output as a fresh crawl.

Suggested pitch: "We turn official civic requirements into a personalized, evidence-backed roadmap showing prerequisites, parallel steps, and what the user can do next." Describe the selected demonstrated improvement over existing guidance, without claiming that NSWS lacks features that were not fully inspected. Our progress is a personal preparation checklist, not official government application tracking.

## 7. Decisions still needed

- Exact jurisdiction and two civic workflows, selected using evidence availability rather than name recognition.
- AI provider/model and accessible team credentials/budget.
- Hosting targets for Vite and the Express API, alongside the existing Neon and Clerk services.
- Whether organizers publish any later constraints on preparation, reused code, or external services.

These decisions do not require replacing the existing stack. The first two hours should settle them before feature implementation diverges.

## Change manifest

| Item | Change |
|---|---|
| `HACKATHON_IMPLEMENTATION_PLAN.md` | Revised for NSWS overlap, source strategy, dependency-focused scope, shared contracts, ownership, 36-hour checkpoints, additional acceptance checks and teammate AI starting prompts. |
| Repository source and configuration | Inspected remotely; unchanged. |
| Database and deployment | Unchanged; no migration or deployment performed. |

Compilation is not applicable to this planning document. Repository/CI statements refer to the previously inspected commit; no fresh repository inspection or local application tests were performed for this document revision.


## 8. Copy-paste starting prompts for teammates

Give each teammate this complete revised plan along with their prompt. This local document has not been pushed to GitHub, so their AI should not assume it exists in their repository. `docs/CONTRACTS.md` and the new feature folders are proposed work, not completed files. Each prompt asks the AI to inspect the latest checkout before implementation; the plan's repository inventory is a dated snapshot.

### Prompt for Soham

```text
I am Soham, working with Razeen, Dhruv and Sahil on a 36-hour hackathon. Help me implement my assigned part of PSWB02, Municipal Bureaucracy Path Visualizer.

Repository: https://github.com/SohamShirke473/hackathon
Read the attached HACKATHON_IMPLEMENTATION_PLAN.md, repository instructions and current code before editing. The previously inspected template used npm workspaces, React/Vite/TypeScript/Tailwind/Clerk/TanStack Query, and Express/Zod/Drizzle/Neon PostgreSQL. Verify the current checkout and preserve existing work.

Product: two reviewed civic workflows in one selected jurisdiction. Produce a personalized, cited dependency roadmap with prerequisites, blockers, next actions and declared existing documents. NSWS Know Your Approvals already handles approval discovery and other related functions. Treat it as existing work and a possible official source; do not claim its current interface lacks dependency planning without verifying that.

I own api/src/modules/ingestion/ and assistant/, backend route registration, backend environment additions, dependency coordination and CI. Razeen owns the knowledge schema, evidence publication and shared applicability/readiness/progress evaluator. Sahil owns graph rendering and roadmap persistence. Dhruv owns the application UI.

First:
1. Inspect the template and the revised plan. Identify the smallest source-to-draft and task-to-roadmap integration paths.
2. With Razeen's agreed definitions, establish docs/CONTRACTS.md and one common fixture before integration. Use the plan's proposed contracts; do not independently redefine them.
3. Help compare the selected scenario with NSWS and gather the exact official source URLs.

Implement bounded retrieval from selected accessible official HTML/text-PDF sources, storing source versions and exact evidence with extraction drafts. Validate structured model output; unresolved facts remain unresolved. Never auto-publish extracted requirements. Add task interpretation and clarification through the agreed POST /api/assistant/resolve contract. For ready requests, call Razeen's evaluator; do not generate authoritative graph nodes with the LLM. Keep provider credentials server-side.

First deliverable: one real official source becomes a validated evidence-linked draft, and a task reaches the shared roadmap fixture through an explicit adapter. Clearly label mocked integration. If workflow, provider or contract details are missing, ask targeted questions and continue independent scaffolding; do not invent civic rules or API availability.

Defer embeddings, broad crawling and admin polish. Coordinate shared-file changes; do not modify teammates' modules. Run focused extraction/error-handling tests and the repository's checks. End each update with a change manifest, verification results, unresolved dependencies and exact handoff details. Verify each changed file compiles/typechecks before moving to the next file.
```

### Prompt for Dhruv

```text
I am Dhruv, working with Razeen, Soham and Sahil on a 36-hour hackathon. Help me implement my assigned part of PSWB02, Municipal Bureaucracy Path Visualizer.

Repository: https://github.com/SohamShirke473/hackathon
Read the attached HACKATHON_IMPLEMENTATION_PLAN.md, repository instructions and current code before editing. The previously inspected frontend was React with Vite, TypeScript, Tailwind, React Router, Clerk and TanStack Query. Verify the current checkout and preserve existing work; keep the existing stack.

Product: two reviewed civic workflows in one selected jurisdiction. A user describes a task, answers necessary clarifications, declares documents already available, and receives a sourced dependency roadmap showing blockers and next actions. NSWS already offers approval discovery and related functions. Our demo must show useful dependency planning without unsupported claims of uniqueness.

I own web/src/features/navigator/, features/roadmaps/, frontend pages/routing/layout, API hooks, the step/evidence drawer, and responsive states. Sahil owns features/graph/ and roadmap persistence APIs. Soham owns ingestion and task interpretation. Razeen owns knowledge, evidence and the shared rule evaluator.

First inspect docs/CONTRACTS.md if available and the revised plan's proposed contracts. Use the same fixture as Sahil. If the contract is missing, request it and isolate temporary fixture access behind an adapter; do not invent a separate API.

Build:
- Task input with jurisdiction/context and clarification questions.
- Relevant existing-document/prerequisite declarations, labelled user-reported.
- A roadmap page embedding Sahil's graph through agreed props/callbacks.
- Next-action and blocker panels displaying server-derived results.
- Step details with application links, dependency explanations, official excerpts and source review dates.
- Saved-roadmap and completion controls using Clerk and TanStack Query.
- Loading, unsupported, unresolved, error and narrow-screen checklist views.

Do not implement graph layout, a second dependency engine, or backend tables. Evidence drawers must distinguish official requirements from supplementary guidance. Checklist completion is not government approval.

First deliverable: task input -> clearly synthetic shared roadmap fixture -> selected step -> dependency evidence and next-action panel. Then connect Soham's resolve API and Sahil's saved-roadmap APIs. Do not present fixtures as live government guidance or persisted data.

Ask targeted questions for missing product decisions while continuing independent UI work. Defer the admin dashboard until the main flow works. Coordinate dependency/lockfile changes with Soham. Verify the actual browser flow and applicable build/lint checks. End each update with a change manifest, verification results, unresolved dependencies and handoff details. Verify each changed file compiles/typechecks before moving to the next file.
```

### Prompt for Sahil

```text
I am Sahil, working with Razeen, Soham and Dhruv on a 36-hour hackathon. Help me implement my assigned part of PSWB02, Municipal Bureaucracy Path Visualizer.

Repository: https://github.com/SohamShirke473/hackathon
Read the attached HACKATHON_IMPLEMENTATION_PLAN.md, repository instructions and current code before editing. The previously inspected template used React/Vite/TypeScript and an Express/Zod/Drizzle/Neon PostgreSQL API with Clerk. Verify the current checkout and preserve existing work.

Product: two reviewed civic workflows in one selected jurisdiction. Show an evidence-backed dependency roadmap with conditional requirements, blockers, parallel preparation and next actions. NSWS already provides approval discovery and other related features; do not assume it lacks a dependency experience or claim a graph visualization alone is unique.

I own web/src/features/graph/, api/src/modules/roadmaps/, and deployment integration preparation. Dhruv owns the enclosing page, hooks and evidence drawer. Razeen owns the knowledge schema and shared applicability/readiness/progress evaluator. Soham owns ingestion, interpretation, API route registration, dependencies and CI.

First inspect docs/CONTRACTS.md if available and the revised plan's proposed contracts. Agree on one shared fixture and graph props/callbacks with the frontend contract. Missing contracts should be explicit adapter dependencies, not independently invented rules.

Build a React Flow visualization with automatic layout, selectable steps, prerequisite direction, blocker highlighting, understandable alternatives and supported parallel branches. Keep applicability, readiness, user-reported completion and evidence status distinct. Return selection/completion events to Dhruv's page; do not duplicate his drawer or fetch hooks.

Implement owner-scoped save/list/get/progress APIs using the existing modular backend patterns. Obtain the owner from Clerk. Validate every step/requirement ID against the pinned procedure version. Create graphs from trusted server data; reject client-authored rules. Call Razeen's evaluator after progress updates rather than implementing another rules engine. Preserve downstream self-reported completion with a warning when a prerequisite is unchecked.

First deliverable: shared synthetic fixture -> graph selection -> visible blocker and next-action change through the shared evaluator adapter. Then persist and restore real evaluated roadmaps. Clearly label mocked adapters until integrated.

Coordinate database definitions/migrations with Razeen and dependencies/route mounting with Soham. Do not modify their owned files independently. Test cross-user access, invalid IDs, save/reload, version pinning and completion reversal. Prepare deployment configuration with agreed hosting details; do not claim deployment until actually verified. End each update with a change manifest, verification results, unresolved dependencies and handoff details. Verify each changed file compiles/typechecks before moving to the next file.
```
