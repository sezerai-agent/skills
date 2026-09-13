---
name: sezer-ai-mvc
description: >
  Evidence-driven master audit, CodeGraph-assisted architecture analysis, feature-gap detection, and controlled refactoring skill for ASP.NET Core MVC solutions.
  Use to discover solution structure and technologies; audit modular boundaries, dependency direction,
  Clean Architecture / Vertical Slice / Modular Monolith fit, MVC controllers/views/viewmodels,
  application/domain services, EF Core entities/configurations/DbContexts/migrations/database schema expectations,
  security, performance, testing, and cross-layer consistency; then produce traceable findings and a dependency-aware
  refactoring plan. Full audit requires CodeGraph-assisted semantic/dependency analysis. Default mode is READ-ONLY; implementation/refactoring requires explicit authorization.
---

> SEZER-AI-MVC Version: v1.3-test
> Completion-gate and consistency-hardening release based on multi-agent real-project audit feedback.

# SEZER AI MVC — ASP.NET Core MVC Full Audit & Refactoring Planner

## 1. Mission

Perform a repository-wide, evidence-driven audit of an ASP.NET Core MVC solution from solution structure to UI and database design.

The skill must:

1. Discover the actual solution before judging it.
2. Identify the architecture that exists, not the architecture the reviewer wishes existed.
3. Verify architecture, modularity, MVC, application/domain, EF Core/database, security, performance, and testing concerns.
4. Trace important features across layers instead of reviewing files in isolation.
5. Record every material finding with evidence, impact, confidence, and a concrete remediation.
6. Build a dependency-aware refactoring plan.
7. Remain read-only unless the user explicitly authorizes changes.
8. Never claim a fix succeeded without build/test verification.
9. For a Full Audit, perform CodeGraph-assisted semantic/dependency analysis and cross-check it against source/build/EF evidence.
10. Detect missing, incomplete, duplicated, dead, misplaced, and suspicious feature implementation from repository evidence; distinguish defects from product suggestions.
11. When refactoring is authorized, repair materially broken module boundaries and thin controllers by moving business/use-case logic to appropriate application/domain services while keeping HTTP/MVC concerns in Presentation.

This skill is diagnostic first, corrective second.

---

## 2. Non-Negotiable Rules

### 2.1 Evidence before conclusions

Never report a defect solely from naming, folder structure, assumptions, conventions, or memory.

For every finding, gather the strongest available evidence:

- exact file path
- symbol/class/method/property
- line number when available
- project reference or package reference
- configuration/mapping
- migration operation
- route/action/view relationship
- build/test/analyzer output
- generated SQL or database metadata when available

If evidence is incomplete, mark the finding as `Needs Verification` instead of presenting it as fact.

### 2.2 Do not hallucinate repository state

Never invent:

- files
- folders
- projects
- controllers
- views
- tables
- columns
- indexes
- constraints
- migrations
- package versions
- test results
- build results
- runtime behavior

If a required artifact cannot be inspected, say so in the report.

### 2.3 Preserve the existing architecture unless evidence justifies change

Do not automatically convert a project to Clean Architecture, Vertical Slice Architecture, DDD, CQRS, microservices, or Modular Monolith.

Evaluate architecture against:

- actual domain complexity
- module boundaries
- system lifetime
- team constraints when known
- integration complexity
- deployment needs
- maintainability problems demonstrated by evidence

Prefer the smallest architectural change that fixes the demonstrated problem.

### 2.4 Audit mode is read-only

Default mode: `READ_ONLY_AUDIT`.

In audit mode, do not:

- edit source files
- create migrations
- apply migrations
- modify package references
- run destructive database commands
- delete code
- reformat the repository
- commit or push changes

Creating requested audit/report files is allowed.

### 2.5 Refactoring requires explicit authorization

Enter `REFACTOR_MODE` only when the user explicitly asks to implement/fix/refactor.

Before modifications:

1. identify the approved phase/scope
2. capture baseline build status
3. capture baseline relevant tests
4. identify blast radius
5. preserve public behavior unless change is explicitly requested

After each meaningful refactoring phase:

1. build
2. run relevant tests
3. run broader tests when feasible
4. report failures honestly
5. show changed files and remaining risks

### 2.6 Database truth levels

Treat these as different evidence levels:

1. C# entity model
2. EF Core configuration/conventions
3. DbContext model
4. migration history
5. generated migration SQL
6. live database schema/metadata

Never claim the live database exactly matches EF Core merely because entities or migrations exist.

If live database access is unavailable, report `Expected Schema`, not `Actual Schema`.

### 2.7 Security findings require security evidence

Avoid speculative vulnerability claims. Distinguish:

- exploitable/confirmed
- high-confidence code issue
- risky configuration
- missing defense-in-depth control
- recommendation/hardening opportunity

### 2.8 Severity is not effort

Do not lower severity because a fix is expensive.
Do not raise severity because a fix is easy.

Track severity and effort separately.

### 2.9 CodeGraph analysis is mandatory for Full Audit

A `Full Audit` is not complete until a CodeGraph-compatible semantic/dependency analysis has been executed against the repository revision being reviewed.

Use the installed CodeGraph implementation and only documented capabilities/commands exposed by that installation. Do not invent CodeGraph command names.

Required CodeGraph evidence, where the installed implementation exposes equivalent capabilities:

- project/module summaries
- symbol and call relationships
- callers/callees for high-risk edits
- circular dependency detection
- dependency/impact or blast-radius analysis
- dead/unused import evidence
- complexity/hot-path evidence
- architecture/design gap evidence when project design documentation exists

CodeGraph is an evidence source, not the sole source of truth. In .NET, framework-driven behavior such as DI registration, EF Core model/schema mapping, reflection, conventions, generated code, runtime dispatch, and Razor behavior can be only partially visible to static graph tools. Cross-check CodeGraph results against direct source inspection, project files, build/analyzer output, EF Core metadata/migrations, tests, and live DB metadata when available.

If CodeGraph cannot run:

- continue only if useful to the user
- mark the audit `PARTIAL — CODEGRAPH NOT VERIFIED`
- do not claim `Full Audit Complete`
- list exactly which graph-dependent checks remain unverified

### 2.10 Product-intent inference must be evidence bounded

The skill may infer missing/incomplete features only from repository evidence such as:

- README/specification/ADR/docs
- navigation/menu entries
- routes/endpoints/actions
- Views/ViewModels/forms
- tests/test names
- entities/schema/migrations
- TODO/FIXME/NotImplemented markers
- interfaces without required implementation
- UI controls with no reachable backend path
- backend use cases with no reachable UI/API path
- domain state or database fields that imply an unfinished workflow only when corroborated by another artifact

Never invent product requirements from generic industry expectations. Label outputs as one of:

- `CONFIRMED DEFECT`
- `INCOMPLETE IMPLEMENTATION`
- `LIKELY MISSING FEATURE`
- `PRODUCT/UX OPPORTUNITY`
- `NEEDS PRODUCT CONFIRMATION`

### 2.11 Thin controllers, not empty controllers

When controller refactoring is authorized, move business rules, orchestration, persistence access, transaction coordination, and reusable use-case logic out of controllers into the appropriate Application/Domain service/use-case.

Keep presentation/HTTP responsibilities in controllers, including as applicable:

- routing and HTTP verb semantics
- model binding
- ModelState-to-response flow
- redirects and status/result selection
- anti-forgery concerns
- user/request context extraction before passing a neutral value to Application
- view selection and UI-specific message mapping

Do not create services that merely wrap every controller line one-for-one.

---

## 3. Operating Modes

### Mode A — Full Audit

Use when the user requests a full repository assessment.

Run all applicable stages:

1. Discovery
2. Architecture Audit
3. MVC Audit
4. Application/Domain Audit
5. Database Audit
6. Security Audit
7. Performance Audit
8. Testing Audit
9. Cross-Layer Audit
10. Findings Synthesis
11. Refactoring Plan

### Mode B — Focused Audit

Use only the requested dimensions but still perform enough Discovery to avoid false assumptions.

Examples:

- database only
- MVC only
- architecture only
- security only
- performance only

### Mode C — Refactoring Plan Only

Use existing verified findings if available.
If findings are not verified, perform the minimum audit needed before planning.

### Mode D — Implement Approved Refactoring

Only after explicit user authorization.
Execute one approved phase or bounded scope at a time.

### Mode E — Architecture Remediation

Use only when the user explicitly asks the skill to correct the architecture/module structure rather than merely report it.

Mandatory sequence:

1. run Discovery and CodeGraph analysis
2. identify actual architecture and root causes
3. propose the smallest coherent target architecture
4. generate an architecture delta plan (`current -> target`)
5. create/strengthen characterization and architecture tests where needed
6. repair dependency direction and module boundaries in bounded steps
7. thin controllers and move use-case/business logic to appropriate services/use cases
8. rebuild and retest after each bounded step
9. rerun CodeGraph/architecture checks after structural changes
10. stop and report if behavior cannot be preserved or verification fails

Do not mechanically convert every project to Clean Architecture or Modular Monolith. If the current modular structure is materially broken, choose and justify a target such as repaired layered architecture, Vertical Slice, Clean Architecture, or Modular Monolith based on repository evidence.

### Mode F — Feature Completion Analysis

Analyze project intent and implementation coverage. Produce evidence-backed suggestions for:

- features referenced but not implemented
- partially implemented workflows
- orphaned UI/backend/database pieces
- missing validations/business invariants
- missing service/use-case boundaries
- missing tests for business-critical flows
- missing code required to complete a demonstrated workflow

For every proposed addition include target module/layer, proposed classes/interfaces/endpoints/views/migrations/tests, dependency impact, and whether implementation changes externally visible behavior. Do not implement feature additions unless the user explicitly requests implementation.

---

## 4. Stage 0 — Baseline & Scope

Before deep analysis, record:

- repository/solution root
- solution files (`*.sln`, `*.slnx`)
- SDK version / `global.json`
- target frameworks
- build configuration used
- package restore status
- git branch and dirty state when available
- test projects
- database provider(s)
- ASP.NET Core app model(s)

When execution is permitted, prefer baseline commands such as:

```bash
dotnet --info
dotnet sln list
dotnet build --no-restore
dotnet test --no-build
```

Adapt commands to repository constraints. Do not fabricate command output.

Record baseline failures before interpreting later failures as refactoring regressions.

---

## 5. Stage 1 — Discovery

### Goal

Create a reliable inventory of the solution, projects, technologies, modules, dependencies, entry points, MVC surface, persistence, and tests.

### 5.1 Solution inventory

Inspect:

- `.sln` / `.slnx`
- `Directory.Build.props`
- `Directory.Build.targets`
- `Directory.Packages.props`
- `global.json`
- `NuGet.config`
- project files
- launch settings when relevant

Extract:

- project names
- target frameworks
- project SDKs
- project references
- important package references
- nullable settings
- implicit usings
- analyzers
- language version when explicitly configured

### 5.2 Technology inventory

Detect actual usage, not package presence alone:

- ASP.NET Core MVC
- Razor Views
- Razor Pages if mixed
- Minimal APIs if mixed
- Entity Framework Core
- database provider
- ASP.NET Core Identity
- authentication schemes
- authorization policies
- FluentValidation or other validation libraries
- AutoMapper/Mapster/manual mapping
- MediatR/CQRS if present
- caching
- background services/jobs
- messaging
- external HTTP clients
- logging/telemetry
- testing frameworks

### 5.3 Structural inventory

Map:

- Web/UI projects
- Application projects
- Domain projects
- Infrastructure projects
- shared/common projects
- feature/module projects
- test projects
- migration projects

### 5.4 MVC inventory

Locate:

- Controllers
- Areas
- Views
- Shared Views
- Partials
- Layouts
- ViewComponents
- TagHelpers
- ViewModels
- binding models
- validation attributes/validators

### 5.5 Persistence inventory

Locate:

- `DbContext` classes
- entities
- owned types
- complex/value types
- `IEntityTypeConfiguration<T>` mappings
- model configuration in `OnModelCreating`
- migrations
- seed data
- interceptors
- repositories if used
- unit of work abstractions if used

### 5.6 Deliverable

Produce a concise `Repository Map` containing:

- solution topology
- detected architecture style(s)
- module candidates
- project dependency graph
- MVC surface summary
- database context summary
- test summary
- technologies/packages that materially affect architecture

Do not label the architecture as compliant/non-compliant yet.

---

## 6. Stage 2 — Architecture Audit

### Goal

Determine whether dependencies, module boundaries, responsibilities, and chosen architecture are coherent with the actual system.

### 6.1 Identify the architecture actually present

Classify based on evidence:

- traditional layered/N-tier
- Clean Architecture
- Vertical Slice Architecture
- DDD + Clean Architecture
- Modular Monolith
- hybrid
- unclear/inconsistent

Do not infer architecture from folder names alone.

Use project references, namespace usage, feature ownership, dependency direction, and runtime composition.

### 6.2 Dependency direction

Check:

- Domain depending on Infrastructure
- Application depending on UI/Web
- inner layers referencing outer layers
- module-to-module references
- UI directly depending on persistence implementation where inappropriate
- shared/common project becoming a dumping ground

### 6.3 Circular dependencies

Check project-level and type/namespace-level cycles when tooling allows.

For each cycle record:

- nodes involved
- actual dependency edges
- why the cycle exists
- safest extraction point

### 6.4 Modular boundaries

For each module candidate evaluate:

- ownership of domain concepts
- ownership of persistence
- cross-module calls
- cross-module entity references
- shared DbContext coupling
- shared table coupling
- integration contracts
- direct access to another module's internals
- namespace leakage
- service registration boundaries

A Modular Monolith should show meaningful isolation, not merely a `Modules/` directory.

### 6.5 SOLID / responsibility audit

Look for evidence of:

- controllers doing business logic
- services with unrelated responsibilities
- repositories duplicating EF Core without adding value
- large interfaces with unrelated consumers
- domain services that are actually infrastructure wrappers
- abstractions with only one implementation and no architectural purpose
- service locator usage
- captive dependency / DI lifetime problems

Do not report generic SOLID violations without concrete behavior/design impact.

### 6.6 Architecture fitness

Evaluate whether the current architecture is proportionate.

Flag both:

- under-architecture: uncontrolled coupling, leaking boundaries, tangled dependencies
- over-architecture: excessive layers/abstractions/handlers for simple CRUD with no demonstrated benefit

### 6.7 Architecture findings

IDs: `ARCH-###`.

---

## 7. Stage 3 — MVC Audit

### Goal

Validate the complete Controller → Action → ViewModel → View chain and MVC framework usage.

### 7.1 Controllers

Check:

- controller responsibility and size
- business logic in actions
- data access directly in controllers
- constructor dependencies
- duplicated action logic
- async usage
- cancellation where appropriate
- model state handling
- PRG (Post/Redirect/Get) where appropriate
- error handling
- response/status behavior

### 7.2 Actions and routing

Verify:

- route ambiguity
- conventional vs attribute routing consistency
- area routing
- action names and HTTP verbs
- GET/POST pairs
- anti-forgery protection for browser form mutations
- authorization at controller/action level
- parameter binding
- overposting risk
- open redirect risk where return URLs are used

### 7.3 ViewModels

Check for:

- entity types passed directly to Views
- persistence annotations leaking to UI
- overly broad models
- binding models exposing fields that should not be user-editable
- missing dedicated create/edit/detail/list models when differences are material
- duplicate/inconsistent validation rules
- nullability mismatches

### 7.4 Views

Inspect:

- correct `@model`
- property usage that exists on the model
- null-safety assumptions
- forms/actions/routes alignment
- partial model alignment
- view data / view bag overuse
- business logic in Razor
- repeated markup suitable for partial/component extraction
- unsafe raw HTML usage
- encoding assumptions
- authorization-based visibility vs actual server-side authorization

UI hiding is never a substitute for authorization.

### 7.5 Partials, Layouts, ViewComponents, TagHelpers

Check:

- responsibility boundaries
- model consistency
- hidden service/data access behavior
- duplicate layout concerns
- view components performing excessive orchestration

### 7.6 Validation

Trace validation through:

- browser/client hints when present
- model binding
- data annotations/validators
- application/domain invariants
- database constraints

Do not consider client-side validation sufficient for integrity.

### 7.7 MVC findings

IDs: `MVC-###`.

---

## 8. Stage 4 — Application & Domain Audit

### Goal

Verify responsibility placement, business rule consistency, models, services, and use-case boundaries.

### 8.1 Application services/use cases

Check:

- orchestration vs business rules
- transaction boundaries
- dependency count
- repeated workflows
- direct UI concerns
- direct infrastructure concerns
- return types coupled to MVC or EF Core

### 8.2 Domain rules

Identify important invariants and determine where they are enforced.

Watch for rules duplicated across:

- controllers
- services
- validators
- entities
- database constraints

If the same invariant is implemented differently in multiple places, record inconsistency risk.

### 8.3 Entity / DTO / ViewModel separation

Check for inappropriate reuse across boundaries.

Do not require separate types mechanically; justify separation when responsibilities, security, versioning, binding, or presentation needs differ.

### 8.4 Duplicate logic

Distinguish:

- harmful duplicated business rules
- harmless similar formatting/presentation
- coincidental duplication

### 8.5 Domain model quality

Where a rich domain model exists, assess:

- invariant protection
- aggregate boundaries
- entity identity
- value objects
- domain events
- mutable public state

Where the application is CRUD-oriented, do not force DDD patterns.

### 8.6 Findings

IDs: `APP-###` and `DOM-###`.

---

## 9. Stage 5 — Database / EF Core Audit

### Goal

Trace persistence from C# entities to expected database schema and query behavior.

### 9.1 Entity audit

Inspect:

- primary keys
- alternate/natural keys
- required vs optional properties
- max lengths
- precision/scale
- enums
- date/time types
- concurrency tokens
- navigation properties
- collection initialization
- owned/value types

### 9.2 Configuration audit

Resolve effective configuration from:

1. conventions
2. data annotations
3. Fluent API
4. `IEntityTypeConfiguration<T>`
5. `OnModelCreating`

Check for conflicting or duplicated mapping.

### 9.3 Relationship audit

For each important relationship verify:

- principal/dependent side
- FK property
- required/optional semantics
- one-to-one uniqueness
- one-to-many cardinality
- many-to-many join model
- delete behavior
- cascade cycles/multiple cascade paths risk

### 9.4 Schema integrity audit

Expected schema checks:

- PKs
- FKs
- unique constraints/indexes
- non-unique indexes
- nullability
- max length
- precision/scale
- default values
- computed values
- concurrency columns
- check constraints where business integrity benefits

Do not recommend indexes blindly. Tie an index recommendation to:

- FK lookup/join pattern
- unique invariant
- frequent filter/order pattern
- demonstrated query pattern

### 9.5 Migration audit

Inspect migration history for:

- missing migration relative to current model
- destructive operations
- drop/recreate patterns
- accidental data loss
- renamed columns represented as drop/add
- nullable → non-nullable changes without safe backfill
- incorrect defaults
- FK changes
- cascade changes
- index/unique changes
- large table operations that may lock production

Do not rewrite migration history automatically.

### 9.6 DbContext audit

Check:

- context responsibilities
- module ownership
- context lifetime
- pooling assumptions
- interceptors
- SaveChanges overrides
- transaction handling
- tenant filters/query filters
- soft-delete filters
- audit fields

### 9.7 Query audit

Look for:

- N+1 queries
- unbounded result sets
- premature materialization
- repeated enumeration
- client evaluation concerns
- unnecessary tracking
- missing projection
- cartesian explosion
- inappropriate `Include`
- missing split query where justified
- synchronous EF calls in async web flows
- per-row update/delete loops where set-based operations are appropriate

Do not apply `AsNoTracking` mechanically to entities that will be updated in the same unit of work.

### 9.8 Database truth statement

Every DB report must state one of:

- `Live schema verified`
- `Migration-generated schema verified`
- `Expected schema inferred from EF Core model and migrations`
- `Database state could not be verified`

### 9.9 Findings

IDs: `DB-###`.

---

## 10. Stage 6 — Security Audit

### Goal

Assess security using implementation evidence and defense-in-depth principles.

### 10.1 Authentication

Check:

- authentication scheme configuration
- cookie settings
- token validation when applicable
- login/logout behavior
- external auth configuration when present

### 10.2 Authorization

Check:

- `[Authorize]` / policies
- role/policy usage
- resource ownership checks
- IDOR/BOLA-style access risks
- admin-only operations
- module/tenant boundaries

### 10.3 Request security

Check:

- CSRF protection for cookie-authenticated browser mutations
- model binding / overposting
- file upload validation
- redirect validation
- request size limits where relevant
- rate limiting for abuse-sensitive endpoints when relevant

### 10.4 Data & secrets

Check:

- hard-coded secrets
- committed credentials
- connection strings
- sensitive values in logs
- personal/sensitive data exposure
- encryption/data protection usage where appropriate

### 10.5 Injection and rendering

Check:

- raw SQL construction
- parameterization
- command execution
- path traversal
- HTML rendering / `Html.Raw`
- unsafe deserialization patterns when applicable

### 10.6 Dependencies

When execution/tooling is available, inspect vulnerable dependencies including transitive packages.

Do not invent CVEs.

### 10.7 Security severity

Use:

- Critical
- High
- Medium
- Low
- Informational

IDs: `SEC-###`.

For confirmed/high-severity findings include:

- attack prerequisite
- affected boundary
- realistic impact
- remediation
- validation method

---

## 11. Stage 7 — Performance Audit

### Goal

Find performance problems grounded in request flow, database usage, allocations, I/O, caching, and concurrency.

### 11.1 Database performance

Check:

- N+1
- large Includes
- missing projection
- unbounded queries
- pagination
- index alignment
- repeated queries per request
- unnecessary SaveChanges calls
- tracking overhead
- bulk/set-based operations

### 11.2 Async/I/O

Check:

- `.Result` / `.Wait()` in request paths
- sync-over-async
- avoidable blocking I/O
- missing cancellation propagation where operations are cancellable and long-running
- fire-and-forget work inside requests

### 11.3 Dependency injection / lifetime performance

Check:

- heavy transient construction
- captive dependencies
- inappropriate singleton state
- unnecessary service resolution

### 11.4 Caching

Evaluate only when data characteristics justify it.

Check:

- repeated expensive reads
- cache invalidation strategy
- user/tenant data isolation
- stale-data risk
- cache stampede considerations

Do not recommend caching as a generic cure.

### 11.5 Rendering/web performance

When relevant check:

- repeated ViewComponent/data calls
- oversized responses
- static asset handling
- compression/output caching where safe

### 11.6 Findings

IDs: `PERF-###`.

---

## 12. Stage 8 — Testing Audit

### Goal

Evaluate whether tests protect important behavior and support safe refactoring.

### 12.1 Inventory

Identify:

- unit tests
- integration tests
- MVC/controller tests
- database tests
- authorization/security tests
- end-to-end/browser tests
- architecture tests

### 12.2 Quality

Check:

- important business rules covered
- critical authorization paths covered
- important data integrity behavior covered
- realistic EF behavior when database semantics matter
- brittle implementation-detail tests
- duplicated test setup
- non-deterministic tests
- tests that do not assert meaningful behavior

### 12.3 Refactoring safety gaps

For every high-risk refactoring phase, identify tests that should exist before changing behavior.

Do not equate raw line coverage with quality.

### 12.4 Findings

IDs: `TEST-###`.

---

## 13. Stage 9 — Cross-Layer Audit

### Goal

Find defects that cannot be reliably detected by reviewing one layer at a time.

This stage is mandatory for a full audit.

### 13.1 Feature trace

For representative and high-risk features, trace:

```text
Route
  -> Controller
  -> Action
  -> Input/Binding Model
  -> Application Service / Use Case
  -> Domain Rules
  -> Entity
  -> EF Configuration
  -> DbContext
  -> Migration
  -> Expected Table/Constraints
  -> Output/ViewModel
  -> View/Partial/ViewComponent
```

### 13.2 Cross-layer inconsistency classes

Look for:

#### UI ↔ ViewModel

- View references missing/nullable properties incorrectly
- partial receives incompatible model
- hidden fields expose mutable values unnecessarily

#### ViewModel ↔ Controller

- fields rendered but never populated
- fields accepted on POST but should not be mutable
- validation expectations differ

#### Controller ↔ Application

- duplicated business rules
- controller bypasses required service/use case
- inconsistent transactions

#### Application ↔ Domain

- domain invariant enforced only in UI/application
- entities allow invalid state used elsewhere

#### Domain ↔ EF Mapping

- required domain value mapped nullable
- value object flattened incorrectly
- relationship cardinality differs from domain intent

#### EF Mapping ↔ Migration

- mapping expects index/constraint absent from migration
- migration behavior differs from current configuration
- rename represented destructively

#### Migration ↔ Database

If live schema access exists, detect drift.
Otherwise explicitly mark this comparison unverified.

#### Authorization ↔ UI

- button hidden but endpoint unprotected
- endpoint protected but UI exposes impossible path
- ownership check missing after model binding

#### Module ↔ Database

- module directly queries another module's internal tables/entities
- shared schema creates hidden coupling
- transaction crosses module boundaries without design rationale

### 13.3 Findings

IDs: `XLAYER-###`.

Cross-layer findings should reference all involved files/components.

---

## 14. Finding Model

Every finding must use this schema.

```markdown
### <ID> — <Short title>

- Severity: Critical | High | Medium | Low | Informational
- Confidence: Confirmed | High | Medium | Needs Verification
- Category: <Architecture/MVC/Domain/Database/Security/Performance/Testing/Cross-Layer>
- Location:
  - `path/to/file.cs:<line>`
  - `path/to/other.cs:<line>`
- Evidence: <what was actually observed>
- Problem: <why this is wrong or risky>
- Impact: <real consequence>
- Recommendation: <specific remediation>
- Validation: <how to prove the remediation works>
- Effort: XS | S | M | L | XL
- Dependencies: <finding IDs or prerequisites>
- Refactoring Phase: <phase number/name>
```

### Severity rubric

#### Critical

Likely severe security compromise, irreversible/major data integrity loss, or system-wide production failure with realistic trigger.

#### High

Significant security/integrity/correctness/architecture problem with substantial impact or strong likelihood of failure.

#### Medium

Meaningful maintainability, reliability, performance, or correctness issue that should be planned.

#### Low

Localized debt, minor risk, or improvement with limited immediate impact.

#### Informational

Observation, optional modernization, or hardening recommendation without demonstrated defect.

---

## 15. Finding Quality Gates

Before including a finding, ask:

1. Did I inspect the relevant code/configuration?
2. Can I cite the exact evidence?
3. Am I distinguishing fact from inference?
4. Is this actually harmful in this repository?
5. Am I recommending a solution proportionate to the problem?
6. Could the recommendation introduce a regression?
7. Is another finding the root cause, making this one secondary?

Merge duplicate findings across categories when they share one root cause.

---

## 16. Audit Report

For a full audit, produce the following sections.

```markdown
# ASP.NET Core MVC Audit Report

## 1. Executive Summary
- Scope
- Audit mode
- Build baseline
- Test baseline
- Overall assessment
- Critical findings
- High findings

## 2. Repository & Technology Map

## 3. Architecture Assessment

## 4. MVC Assessment

## 5. Application & Domain Assessment

## 6. Database / EF Core Assessment
- Database truth level

## 7. Security Assessment

## 8. Performance Assessment

## 9. Testing Assessment

## 10. Cross-Layer Assessment

## 11. Findings Register

| ID | Severity | Confidence | Area | Summary | Effort | Phase |
|----|----------|------------|------|---------|--------|-------|

## 12. Positive Findings
Document architecture or implementation choices that are already sound and should be preserved.

## 13. Unknowns / Verification Gaps

## 14. Refactoring Plan
```

Do not produce a report consisting only of problems. Record important strengths so refactoring does not destroy them.

---

## 17. Refactoring Plan

### Principle

Order work by dependency and risk, not merely by severity.

Default phases:

### Phase 0 — Baseline & Safety Net

- establish clean/reproducible build baseline
- document failing tests that pre-exist
- add characterization/regression tests for high-risk behavior when needed
- capture database/migration state

### Phase 1 — Critical Security & Data Integrity

- exploitable security issues
- authorization failures
- destructive schema risks
- missing critical integrity constraints
- confirmed data corruption risks

### Phase 2 — Architecture Stabilization

- circular dependencies
- reversed dependency direction
- module boundary leaks
- invalid service lifetimes
- root coupling that blocks later refactoring

### Phase 3 — Persistence & Database

- mapping correctness
- constraints
- migrations
- query correctness
- N+1 / high-impact query problems
- index changes backed by query/integrity evidence

### Phase 4 — Application & Domain

- duplicate/conflicting business rules
- responsibility movement
- transaction boundaries
- DTO/entity boundary corrections

### Phase 5 — MVC/UI Boundary

- ViewModels
- overposting
- controller thinning
- validation alignment
- routing/forms/views consistency

### Phase 6 — Performance & Resilience

- async/blocking issues
- caching where justified
- query optimization
- request-path hot spots

### Phase 7 — Test Reinforcement

- missing integration tests
- security/authorization tests
- database behavior tests
- architecture tests

### Phase 8 — Cleanup & Maintainability

- dead code
- naming
- duplication without business risk
- documentation
- style/analyzer cleanup

### Plan item schema

```markdown
#### RP-<number> — <title>
- Addresses: <finding IDs>
- Goal: <desired outcome>
- Prerequisites: <other RP items or none>
- Files/Projects likely affected: <verified paths/projects>
- Proposed changes: <specific but not prematurely code-level>
- Behavior changes: None | <explicit description>
- Database migration required: Yes | No | Maybe
- Tests required before: <tests>
- Tests required after: <tests>
- Validation commands: <commands appropriate to repository>
- Rollback concern: <risk>
- Effort: XS | S | M | L | XL
- Risk: Low | Medium | High
```

---

## 18. Refactor Mode Execution Protocol

When the user explicitly requests implementation:

### 18.1 Confirm scope from existing instruction

Do not expand beyond the approved phase/findings.

### 18.2 Re-check affected files

Repository state may have changed since the audit.

### 18.3 Baseline

Run/record relevant build and tests before modifying files when possible.

### 18.4 Change in bounded increments

Prefer coherent, reviewable changes.
Avoid unrelated cleanup.

### 18.5 Database changes

For EF Core changes:

- modify model/configuration deliberately
- generate migration only when explicitly within scope
- inspect migration before accepting it
- inspect generated SQL for high-risk production changes when tooling permits
- never auto-apply production migrations

### 18.6 Verify

At minimum:

1. build affected projects/solution
2. run targeted tests
3. run broader test suite if feasible
4. inspect warnings/errors
5. verify migration/model consistency for database changes

### 18.7 Report truthfully

Use one of:

- `VERIFIED`: requested validation passed
- `PARTIALLY VERIFIED`: some validation could not run
- `FAILED VERIFICATION`: validation failed

Never say "fixed" solely because code was edited.

---

## 19. Architecture-Specific Checks

### Clean Architecture

Verify:

- Domain has no outer-layer dependency
- Application depends on Domain, not Infrastructure implementation
- Infrastructure implements required ports/contracts
- Web/Presentation composes dependencies
- persistence details do not leak into Domain
- abstractions serve actual boundaries rather than ceremony

### Vertical Slice Architecture

Verify:

- feature cohesion
- minimal cross-slice coupling
- shared/common area remains small and purposeful
- business rules are not duplicated across handlers
- vertical slices do not become hidden layered architecture with global services

### Modular Monolith

Verify:

- modules correspond to meaningful business boundaries
- module internals are not directly referenced by peers
- integration occurs through explicit contracts/messages/services
- database ownership is defined
- cross-module transaction strategy is deliberate
- shared kernel is constrained
- host/composition root does not become business-logic hub

### DDD

Only evaluate DDD tactical patterns when the repository actually uses or needs them.

Verify:

- aggregates protect real invariants
- value objects model real concepts
- domain events have clear semantics
- repositories align to aggregate boundaries when repositories are used

Do not penalize CRUD domains for not using DDD.

---

## 20. ASP.NET Core Framework Checks

Inspect framework usage appropriate to the target version and repository conventions:

- `Program.cs` / composition root
- service registration
- options/configuration
- middleware order
- routing
- static files
- authentication before authorization
- exception handling / ProblemDetails where applicable
- forwarded headers/proxy behavior when deployed behind proxies
- HTTPS/HSTS according to environment
- antiforgery in browser form flows
- health checks when operationally required
- rate limiting where abuse risk justifies it
- output caching only for safe responses

Do not modernize framework APIs merely because newer APIs exist unless the current usage is problematic or the user requests an upgrade.

---

## 21. DI Audit Rules

Check lifetimes carefully:

- Singleton must not capture scoped dependencies.
- DbContext is normally scoped to the request/unit of work.
- Avoid service locator (`IServiceProvider.GetService`) in domain/application logic.
- Prefer constructor injection for required dependencies.
- Detect classes with excessive dependency count as a responsibility smell, not an automatic defect.

If a lifetime mismatch is only theoretical, identify whether the actual registration proves it.

---

## 22. EF Core Safety Rules

- Treat migrations as code requiring review.
- Avoid automatic production migration execution unless the deployment model explicitly requires and safely supports it.
- Prefer projections for read-only DTO/ViewModel queries when full entities are unnecessary.
- Detect N+1 from query/use patterns, not from navigation properties alone.
- Use tracking when mutation requires it; use no-tracking intentionally for read paths.
- Evaluate split queries vs single queries according to graph size and consistency needs.
- Recommend compiled queries only when measurement/hot-path evidence justifies complexity.
- Avoid repository abstractions that merely duplicate `DbSet` unless they enforce meaningful domain/module boundaries.

---

## 23. Security Principles

Apply:

- least privilege
- defense in depth
- secure by default
- explicit trust boundaries
- server-side authorization
- server-side validation
- parameterized data access
- secret separation
- safe logging

For threat reasoning, consider STRIDE categories when applicable, but do not force a full STRIDE table for trivial code paths.

---

## 24. Performance Principles

Optimization must be evidence-informed.

Priority order:

1. correctness
2. data integrity/security
3. algorithm/query behavior
4. I/O and database round trips
5. allocations/low-level micro-optimization

Do not recommend complex optimization without material expected benefit.

---

## 25. Testing Principles

Prefer behavior-focused tests.

Use appropriate test levels:

- unit tests for isolated domain/business rules
- integration tests for EF/database behavior and application boundaries
- MVC/web integration tests for routing, filters, model binding, auth, antiforgery, and responses
- E2E/browser tests for critical user journeys when justified
- architecture tests for dependency/module rules when architecture stability is important

Before risky refactoring, add characterization tests when behavior is insufficiently protected.

---

## 26. Output Language

Use the user's language for reports unless explicitly instructed otherwise.

Keep technical identifiers, code symbols, commands, framework names, and file paths unchanged.

---


## 26A. Mandatory CodeGraph-Assisted Analysis Protocol

### Objective

Build a semantic map before large architectural conclusions or refactors. The map supplements direct source analysis.

### Deterministic protocol

1. Bind analysis to the current repository/revision/worktree.
2. Index/analyze the entire solution scope unless the repository is too large; if narrowed, disclose exclusions.
3. Produce a module/project summary.
4. Find circular dependencies.
5. Identify high-complexity/hot-path symbols when supported.
6. For every proposed structural edit, obtain callers/callees or equivalent edit/impact context.
7. For module extraction/moves, obtain blast-radius/impact evidence first.
8. Compare graph edges against project references and namespace/module rules.
9. If architecture/design documentation exists, compare code against documented design and report verified gaps.
10. Rerun relevant graph checks after architecture refactoring.

### Required report block

```markdown
## CodeGraph Analysis
- Status: VERIFIED | PARTIAL | NOT AVAILABLE
- Repository/revision analyzed: ...
- Scope: ...
- Modules discovered: ...
- Circular dependencies: ...
- High-risk dependency edges: ...
- Impact-analysis findings: ...
- Complexity/hot-path findings: ...
- Design/code gaps: ...
- Known blind spots requiring direct verification: ...
```

Never treat absence of a CodeGraph edge as proof that no runtime/framework dependency exists.

---

## 26B. Deterministic MVC View Contract Audit

For every reachable Razor View, build a `View Contract Record`.

```text
Route/Link/Form
  -> Controller.Action
  -> HTTP verb + authorization + antiforgery
  -> Input/Binding model
  -> Application use case/service
  -> Output/ViewModel
  -> View path
  -> @model
  -> properties rendered
  -> forms/links generated by the view
  -> POST/target action
```

### Mandatory checks per View

- View is reachable, intentionally partial, or confirmed orphaned.
- resolved View path matches controller/action conventions or explicit path.
- `@model` type matches the object passed by the action.
- every strongly typed property reference exists and has compatible nullability/type semantics.
- `asp-for`, `asp-action`, `asp-controller`, `asp-route-*`, form method and route values resolve to a valid target.
- POST/PUT-like browser mutations have appropriate anti-forgery protection unless a documented alternative applies.
- UI authorization visibility is paired with server-side authorization.
- validation messages correspond to actual validation rules.
- select/list data required by the View is populated on both initial GET and validation-failure redisplay paths.
- partial/ViewComponent model contract matches each call site.
- ViewBag/ViewData keys are traced from producer to consumer; flag unproven or inconsistent keys.
- business decisions in Razor are moved toward ViewModel/application logic when they exceed presentation formatting/branching.
- duplicated markup is quantified before proposing extraction.
- raw HTML/rendering bypasses are security-reviewed.

### Orphan detection

Classify:

- `ORPHAN_VIEW`: no route/action/component/reference found and no framework convention justifies it.
- `BROKEN_VIEW_CONTRACT`: reachable but model/form/route contract is inconsistent.
- `DUPLICATE_VIEW_LOGIC`: same nontrivial presentation/business behavior repeated across Views.
- `MISSING_VIEW_PATH`: action expects a view that cannot be resolved from inspected artifacts.

Never delete an orphan candidate without checking dynamic view names, Areas, localization/themes, runtime conventions, and references not visible to the analyzer.

---

## 26C. Deterministic Real Database Schema Reconciliation

### Evidence hierarchy

Build three schemas separately:

1. `MODEL_SCHEMA`: effective EF Core model from entities + configuration + conventions.
2. `MIGRATION_SCHEMA`: schema implied by ordered migrations/model snapshot/generated SQL.
3. `LIVE_SCHEMA`: schema obtained from the actual database metadata, only when access is available.

### Reconciliation matrix

For every relevant table/entity compare:

- table/schema name
- PK columns and ordering
- column name/type/provider type
- nullability
- max length
- precision/scale
- defaults/computed columns
- identity/generated strategy
- concurrency token/version column
- FK target and columns
- delete behavior
- unique constraints
- indexes and index uniqueness/order/filter where available
- check constraints
- owned/table-splitting/TPT/TPH mapping as applicable

Classify each difference:

- `MODEL_MIGRATION_DRIFT`
- `MIGRATION_LIVE_DRIFT`
- `MODEL_LIVE_DRIFT`
- `EXPECTED_PROVIDER_DIFFERENCE`
- `UNVERIFIED`

### Safety

- Never auto-apply a production migration.
- Never generate destructive SQL and call it safe without inspecting the delta.
- For live schema, use read-only metadata queries where possible.
- Before proposing column drops/renames/type narrowing/nullability tightening, include data-preservation and rollback strategy.

---

## 26D. Deterministic Modular Monolith Boundary Audit

### Module manifest

For each module construct:

```text
Module
- owned domain types
- owned application/use cases
- exposed contracts
- internal implementation
- persistence ownership / DbContext / tables
- inbound dependencies
- outbound dependencies
- events/messages
- composition/DI registration
- MVC/UI entry points
```

### Boundary rules

Flag with concrete edges:

- module A directly references module B internals
- module A queries module B tables/DbSet directly without an approved shared-data design
- domain type from one module is used as another module's persistence/UI contract
- shared project contains module-specific business rules
- bidirectional module dependency
- cross-module transaction coupling that prevents isolation
- cross-module navigation properties creating persistence coupling
- duplicated ownership of the same business invariant
- module has no clear public contract and exposes implementation classes
- composition root cannot determine module registration cleanly

### Architecture scoring

For each module score with evidence, not intuition:

- Cohesion: 0-5
- Boundary integrity: 0-5
- Dependency direction: 0-5
- Data ownership: 0-5
- Contract quality: 0-5
- Testability/isolation: 0-5

Scores must link to findings. A low score alone is not a finding.

### Repair algorithm when authorized

1. identify the cycle/leak/root coupling
2. select ownership of the business concept
3. define or repair the module public contract
4. move abstractions/contracts only when they represent a real boundary
5. remove forbidden project/namespace/data references
6. replace direct cross-module persistence calls with explicit application contracts/events only when justified
7. update DI/composition
8. migrate controllers/use cases to the repaired boundary
9. add architecture tests enforcing the dependency rule
10. build/test
11. rerun CodeGraph boundary/cycle/impact analysis

---

## 26E. Controller-to-Service / Use-Case Refactoring Engine

### Controller logic classification

Classify every nontrivial controller statement into:

- `HTTP/PRESENTATION` — remains in controller
- `APPLICATION ORCHESTRATION` — move to application use case/service
- `DOMAIN RULE` — move to domain entity/value object/domain service when appropriate
- `PERSISTENCE` — move behind the module/application persistence boundary
- `CROSS-CUTTING` — middleware/filter/decorator/infrastructure as appropriate
- `MAPPING` — presentation mapping or application mapping depending on direction

### Mandatory smells

Flag controllers that contain:

- direct `DbContext`/repository queries or SaveChanges
- transactions
- business calculations/rules
- state transitions
- multi-service orchestration that represents one reusable use case
- repeated validation/business branches across actions
- external integration calls
- file/storage/email/payment logic
- repeated mapping that belongs to a stable application boundary

### Target shape

Prefer:

```text
Controller
  -> validate/bind HTTP input
  -> call one coherent use case/service operation
  -> map result to IActionResult/View

Application Use Case/Service
  -> orchestrate workflow
  -> enforce application-level authorization/policy where applicable
  -> call domain behavior
  -> coordinate persistence/integration
  -> return transport-neutral result
```

Do not move `IActionResult`, `ViewResult`, `HttpContext`, `ModelStateDictionary`, Razor-specific types, or presentation redirects into core/domain services unless the architecture explicitly chooses a Web-only application layer and the trade-off is documented.

---

## 26F. Dead, Duplicate, Incomplete, and Missing Code Analysis

### Dead code evidence

Use multiple signals:

- compiler/analyzer warnings
- CodeGraph references/callers/imports
- route reachability
- DI registration and resolution
- reflection/configuration conventions
- tests
- Razor/View references
- serialization/model binding usage

Classify as `CONFIRMED DEAD` only when framework/dynamic usage has been ruled out with high confidence. Otherwise use `DEAD-CODE CANDIDATE`.

### Duplicate code

Separate:

- lexical duplication
- duplicated orchestration
- duplicated business invariant
- duplicated query
- duplicated View markup

Prioritize duplicated business rules over harmless textual similarity.

### Incomplete code

Search for and trace:

- TODO/FIXME/HACK
- `NotImplementedException`
- placeholder returns/defaults
- empty catch/handlers
- interfaces/classes with unreachable or missing implementation
- UI action with no backend completion
- backend operation with no final persistence/result path
- migration/entity fields never integrated into use cases
- branches that intentionally/accidentally do nothing
- disabled/skipped tests that point to missing behavior

### Feature-gap proposal schema

```markdown
#### FEAT-### — <feature or completion proposal>
- Classification: INCOMPLETE IMPLEMENTATION | LIKELY MISSING FEATURE | PRODUCT/UX OPPORTUNITY | NEEDS PRODUCT CONFIRMATION
- Evidence: <docs/routes/UI/tests/schema/code>
- User/business intent inferred: <bounded statement>
- Existing pieces: <what already exists>
- Missing pieces: <what is absent>
- Proposed module: <owner>
- Proposed code additions/changes:
  - Application: ...
  - Domain: ...
  - Infrastructure/DB: ...
  - MVC/UI: ...
  - Tests: ...
- Architecture impact: ...
- DB migration: Yes | No | Maybe
- Product confirmation required: Yes | No
- Confidence: High | Medium | Low
```

---

## 26G. Architecture Recommendation and Auto-Remediation Contract

After audit, produce exactly one primary architecture recommendation:

- `KEEP AND REPAIR CURRENT ARCHITECTURE`
- `REPAIR AS LAYERED/N-TIER`
- `EVOLVE TO VERTICAL SLICE`
- `EVOLVE TO CLEAN ARCHITECTURE`
- `EVOLVE TO MODULAR MONOLITH`
- `HYBRID — <explicit rationale>`

The recommendation must include:

- current architecture evidence
- observed pain/root causes
- target architecture
- why rejected alternatives are not preferred
- module/project boundaries
- dependency rules
- data ownership rules
- controller/application/domain responsibilities
- migration/refactor sequence
- expected benefits
- costs/risks
- architecture tests to prevent regression

When Architecture Remediation mode is explicitly authorized and the current modular architecture is objectively broken, the skill must implement the approved target architecture in bounded phases rather than merely report it. Do not proceed past a failed verification gate without reporting the failure.

---

## 26H. Expanded Completion Gates

A `Full Audit` must additionally satisfy all of the following:

- CodeGraph analysis status is VERIFIED, otherwise label the audit partial
- representative MVC View contracts are traced; all high-risk forms/actions are traced
- EF model vs migrations is reconciled; live DB is reconciled when access is available
- module manifest and boundary graph are produced for modular solutions
- controller logic is classified for high-complexity/high-risk controllers
- dead/duplicate/incomplete code analysis is performed
- feature-gap analysis is evidence-bounded
- one primary architecture recommendation is produced
- refactor plan includes architecture enforcement tests

## 27. Completion Criteria

A full audit is complete only when:

- repository inventory is documented
- architecture is identified from evidence
- project/module dependencies are evaluated
- MVC chain is evaluated
- application/domain responsibilities are evaluated
- EF Core mapping/migrations are evaluated
- database truth level is explicitly stated
- security is evaluated
- performance is evaluated
- testing is evaluated
- representative cross-layer traces are completed
- findings use the standard schema
- duplicates/root causes are consolidated
- unknowns are disclosed
- refactoring plan is dependency-aware
- no code was changed unless explicitly authorized
- CodeGraph-assisted analysis completed for a Full Audit, or report is explicitly marked partial
- architecture recommendation is explicit and evidence-backed
- dead/duplicate/incomplete/missing-feature analysis is included

A refactoring implementation is complete only when:

- approved scope is implemented
- relevant build passes or failure is reported
- relevant tests pass or failure is reported
- database/migration changes are reviewed when applicable
- final status is labeled VERIFIED / PARTIALLY VERIFIED / FAILED VERIFICATION

---

## 28. Source Influences

This master skill synthesizes ideas from public .NET/ASP.NET Core skill ecosystems and security-review workflows, including:

- OpenAI `aspnet-core` skill: framework-aware ASP.NET Core review/refactor workflow; respect existing app model; targeted MVC, data, security, testing and performance references.
- codewithmukesh `dotnet-claude-kit`: evidence-based health checks, architecture selection, EF Core guidance, testing, security scan, refactoring/verification workflow.
- novotnyllc `dotnet-artisan`: .NET routing model, cross-domain review, architecture/code/security/testing/performance specialist concerns.
- Microsoft `devsquad-copilot` security review: structured security findings, severity, impact, recommendations, STRIDE/OWASP-oriented review.
- CodeGraph-style semantic code graph analysis: cross-file symbols/calls, impact analysis, circular dependency detection, complexity/hot paths, and design-gap verification where supported.

This file is a new synthesis. It must not assume those external skills are installed at runtime.

---

## 29. Minimal Invocation Examples

### Full read-only audit

```text
Use sezer-ai-mvc to audit this ASP.NET Core MVC repository end-to-end.
Do not modify code. Produce evidence-backed findings and a dependency-aware refactoring plan.
```

### Database-focused audit

```text
Use sezer-ai-mvc in focused audit mode.
Trace Entity -> EF configuration -> DbContext -> migrations -> expected schema -> query patterns.
Do not modify anything.
```

### Cross-layer audit

```text
Use sezer-ai-mvc to trace the Order Edit feature from route/controller through ViewModel,
application/domain, EF Core, migration/schema expectation, and Razor View.
Report cross-layer inconsistencies only.
```

### Implement an approved phase

```text
Use sezer-ai-mvc in REFACTOR_MODE.
Implement only Phase 2 Architecture Stabilization from the approved report.
Build and run relevant tests after each bounded change. Do not expand scope.
```

---

## 30. Deterministic Analysis Toolkit — Mandatory for Full Audit

`sezer-ai-mvc` SHOULD use deterministic repository-analysis scripts whenever execution is available.
The scripts are evidence producers; the LLM is the interpreter, correlator, and planner.

A Full Audit is not considered fully verified unless the applicable deterministic checks have run successfully,
or the final report explicitly marks the missing checks as `NOT_EXECUTED` with the reason.

### 30.1 Required Toolkit Layout

```text
sezer-ai-mvc/
├── SKILL.md                         # or sezer-ai-mvc.md
├── scripts/
│   ├── inventory/
│   │   ├── solution-inventory.ps1
│   │   ├── project-reference-graph.ps1
│   │   └── package-inventory.ps1
│   ├── architecture/
│   │   ├── module-boundary-audit.ps1
│   │   ├── circular-dependency-audit.ps1
│   │   ├── forbidden-reference-audit.ps1
│   │   └── architecture-score.ps1
│   ├── mvc/
│   │   ├── mvc-route-action-view-map.ps1
│   │   ├── view-contract-audit.ps1
│   │   ├── form-post-contract-audit.ps1
│   │   └── controller-complexity-audit.ps1
│   ├── services/
│   │   ├── controller-service-candidate-audit.ps1
│   │   ├── service-responsibility-audit.ps1
│   │   └── application-flow-map.ps1
│   ├── efcore/
│   │   ├── dbcontext-inventory.ps1
│   │   ├── ef-model-inventory.ps1
│   │   ├── migration-inventory.ps1
│   │   ├── migration-drift-audit.ps1
│   │   └── live-schema-audit.ps1
│   ├── quality/
│   │   ├── dead-code-candidate-audit.ps1
│   │   ├── duplicate-code-candidate-audit.ps1
│   │   ├── incomplete-code-audit.ps1
│   │   └── large-file-hotspot-audit.ps1
│   ├── tests/
│   │   ├── test-inventory.ps1
│   │   ├── feature-test-gap-audit.ps1
│   │   └── architecture-test-gap-audit.ps1
│   └── verify/
│       ├── build-verify.ps1
│       ├── test-verify.ps1
│       ├── format-verify.ps1
│       ├── migration-verify.ps1
│       └── audit-diff.ps1
├── schemas/
│   ├── finding.schema.json
│   ├── inventory.schema.json
│   ├── architecture.schema.json
│   ├── mvc-contract.schema.json
│   ├── database.schema.json
│   └── verification.schema.json
└── artifacts/
    ├── evidence/
    ├── reports/
    └── baselines/
```

PowerShell is suggested for portability across Windows-centric .NET repositories.
Equivalent Bash, Python, Roslyn, `dotnet` tools, or compiled helper utilities are acceptable.
The required behavior matters more than the language.

---

## 31. Deterministic Execution Contract

Every script MUST follow these rules where practical:

1. read repository state without modifying source by default
2. accept repository root explicitly
3. never infer a successful result from missing input
4. distinguish `PASS`, `WARN`, `FAIL`, `UNKNOWN`, and `NOT_EXECUTED`
5. emit machine-readable JSON
6. optionally emit human-readable Markdown
7. record the command/tool versions used
8. record timestamp and repository commit when Git is available
9. include exact file/project/module evidence
10. use non-zero exit code for execution failure, not simply for discovered findings
11. never silently swallow analyzer/build/tool errors
12. never mutate migrations or database during audit mode
13. write generated evidence under an audit artifact folder, never inside product source folders unless explicitly configured

Recommended standard invocation shape:

```text
<script> \
  --repo <repository-root> \
  --output <artifact-path> \
  --format json \
  --mode audit
```

Recommended evidence envelope:

```json
{
  "tool": "sezer-ai-mvc",
  "check": "mvc-view-contract",
  "status": "PASS|WARN|FAIL|UNKNOWN|NOT_EXECUTED",
  "repository": "...",
  "commit": "...",
  "timestampUtc": "...",
  "toolVersions": {},
  "inputs": [],
  "findings": [],
  "errors": []
}
```

The LLM MUST NOT rewrite script failures as successful checks.

---

## 32. Repository Inventory Script Requirements

### 32.1 `solution-inventory`

Collect deterministically:

- `.sln` / `.slnx`
- all `.csproj`
- TargetFramework / TargetFrameworks
- SDK style
- OutputType
- Nullable setting
- ImplicitUsings
- LangVersion
- ASP.NET Core hosting projects
- test projects
- worker/service projects
- class libraries
- project references
- central package management
- Directory.Build.*
- Directory.Packages.props
- global.json
- NuGet.config
- appsettings variants
- launch settings presence
- Docker/container files
- CI files

Output a project graph, not just a flat file list.

### 32.2 `project-reference-graph`

Build directed edges:

```text
ProjectA -> ProjectB
```

Detect:

- circular project references
- project reference cycles
- UI -> Infrastructure direct coupling
- Domain -> Infrastructure coupling
- ModuleA -> ModuleB internal implementation references
- Shared project becoming a dumping ground
- test project production references that reverse expected direction

Output both JSON adjacency data and Graphviz/DOT when possible.

### 32.3 `package-inventory`

Record:

- package id
- version
- owning project
- transitive/direct status when obtainable
- EF Core providers
- ASP.NET packages
- authentication packages
- mapping/validation libraries
- logging libraries
- test frameworks
- architecture-test libraries

Do not mark a package as vulnerable without a real advisory source/tool result.

---

## 33. CodeGraph-Assisted Analysis — Mandatory Correlation Layer

For Full Audit, run CodeGraph or an equivalent semantic code-graph analysis where available.
The graph must be treated as a structural evidence source, not as the sole authority.

Collect when supported:

- symbol definitions
- references
- caller/callee edges
- namespace dependencies
- class/interface relationships
- project relationships
- cycles
- fan-in / fan-out
- high-centrality classes
- hot-path classes
- orphan symbols
- apparently unreachable flows
- feature entry points
- change impact candidates

### 33.1 Mandatory Correlation

CodeGraph findings MUST be cross-checked against:

```text
CodeGraph
    + compiler/build
    + project references
    + ASP.NET routing conventions/attributes
    + DI registrations
    + EF Core mappings/migrations
    + runtime-generated behavior when relevant
```

Known limitation rule:

> If a relationship may be generated by runtime DI, conventions, reflection, Razor compilation,
> source generators, EF Core conventions, or framework discovery, CodeGraph absence is NOT proof of absence.

Therefore use confidence levels:

- `CONFIRMED` — graph + source/tool evidence agree
- `HIGH` — strong static evidence, framework ambiguity low
- `MEDIUM` — likely but requires runtime/framework verification
- `LOW` — heuristic candidate only

CodeGraph is REQUIRED for impact analysis before broad refactoring.

---

## 34. Deterministic Modular Monolith Boundary Audit

The skill MUST build a module registry before evaluating modularity.

For every module determine, where present:

```text
Module
├── Domain
├── Application
├── Infrastructure/Persistence
├── Presentation/Web
├── Contracts/Public API
├── Composition Root / DI registration
└── Tests
```

### 34.1 Module Detection Sources

Use evidence from:

- project names
- folder roots
- namespaces
- module registration extensions
- DbContext ownership
- route areas
- contracts/events
- README/docs
- tests
- assembly boundaries

Do not declare a folder a module solely because its name looks like one.

### 34.2 Forbidden Boundary Patterns

Detect and report direct evidence for patterns such as:

```text
ModuleA.Domain -> ModuleB.Infrastructure          FORBIDDEN
ModuleA.Application -> ModuleB.Persistence       FORBIDDEN
ModuleA.Web -> ModuleB internal repository       FORBIDDEN
ModuleA.Infrastructure -> ModuleB internal type  SUSPICIOUS/FORBIDDEN
Domain -> ASP.NET MVC types                      FORBIDDEN
Domain -> EF Core provider-specific code         USUALLY FORBIDDEN
```

Allowed communication SHOULD be explicit via:

- public contracts
- application abstractions
- integration events
- domain events where semantically appropriate
- mediated commands/queries
- published module APIs

### 34.3 Module Ownership Checks

For every important concept determine ownership:

- entity ownership
- DbContext ownership
- migration ownership
- service ownership
- route/controller ownership
- view ownership
- integration contract ownership

Flag shared mutable domain state without clear ownership.

### 34.4 Modularity Score

Produce an evidence-backed score per module:

```text
Boundary integrity        0-20
Dependency direction      0-20
Data ownership            0-20
Public contract quality   0-15
Internal encapsulation    0-15
Testability               0-10
TOTAL                     0-100
```

A score is diagnostic, not authoritative. Every deduction must reference evidence.

### 34.5 Architecture Remediation Rule

If modular architecture is materially broken and the user authorized refactoring:

1. map the current graph
2. select target architecture
3. state why it fits project behavior
4. define module boundaries
5. create/repair contracts
6. remove forbidden references in dependency order
7. move responsibilities without changing behavior unnecessarily
8. add architecture tests
9. build/test after every bounded phase
10. re-run boundary audit and compare before/after

Never perform a repository-wide folder reshuffle without a dependency-aware migration plan.

---

## 35. Deterministic MVC Route → Action → View Contract Audit

Build a normalized MVC contract map.

For every reachable MVC action, collect:

```text
Area
Route
HTTP verb
Controller
Action
Authorization attributes/policies
Input model
ModelState usage
Application/service calls
Returned result type
View name
ViewModel type
Layout/partial/components
POST counterpart
Redirect target
```

### 35.1 View Resolution Checks

Resolve convention-based and explicit views:

```text
return View();
return View(model);
return View("Edit", model);
return PartialView(...);
return ViewComponent(...);
```

Check:

- expected `.cshtml` exists
- model declaration matches action-supplied type
- partial model contracts match callers
- ViewComponent argument contracts match invocation
- layout references exist
- sections required by layout are satisfied where determinable
- view imports/tag helpers do not indicate obviously broken dependencies

Do not claim a view is missing when a custom view engine/runtime location expander is detected but unresolved.
Mark it `UNKNOWN` or `NEEDS_RUNTIME_VERIFICATION`.

### 35.2 Form Contract Checks

For forms determine:

- action target
- HTTP method
- antiforgery expectations
- bound model fields
- validation fields
- hidden IDs
- concurrency tokens
- file inputs
- checkbox semantics
- route values
- submit buttons with alternate actions

Cross-check against POST action parameter/ViewModel.

Flag deterministic mismatches such as:

- form field has no bindable target
- required ViewModel property is never posted
- POST action expects property not present in form and has no other source
- entity is bound directly where overposting risk is clear
- ID from route/form can conflict without reconciliation
- antiforgery missing where policy/framework conventions require explicit presence

### 35.3 ViewModel Contract Graph

Map:

```text
View
  -> ViewModel
      -> Controller Action
          -> Application Service/Handler
              -> DTO/Command
```

Detect:

- Entity exposed directly to View
- persistence-only fields leaking to UI
- duplicated validation rules that disagree
- ViewModel properties never used in View or POST flow
- View fields never mapped to application command
- display-only data missing on validation redisplay path

---

## 36. Controller Complexity and Controller-to-Service Candidate Engine

The skill MUST NOT blindly move all controller code into services.
Instead classify every meaningful controller statement/block.

Classification categories:

```text
HTTP_PRESENTATION
APPLICATION_ORCHESTRATION
DOMAIN_RULE
PERSISTENCE
MAPPING
CROSS_CUTTING
VIEW_PREPARATION
UNKNOWN
```

### 36.1 Allowed Controller Responsibilities

Usually acceptable:

- HTTP verb/route handling
- extracting route/query/form input
- ModelState handling
- invoking application use cases
- selecting View/Redirect/Status result
- lightweight mapping between transport input and application request
- authentication context extraction

### 36.2 Strong Refactor Candidates

Flag controller-contained code such as:

- direct DbContext query/update patterns
- transactions
- multi-step business workflows
- business invariants
- pricing/calculation rules
- permission logic beyond simple policy invocation
- cross-module orchestration
- external API calls
- file processing business logic
- duplicated lookup/bootstrap logic across actions
- repeated entity-to-ViewModel business mapping

### 36.3 Complexity Signals

Capture at minimum:

- action line count
- controller line count
- branch count heuristic
- number of injected dependencies
- number of direct DbContext/repository uses
- number of service calls per action
- duplicate blocks
- exception-handling density

Suggested review thresholds are heuristics only; do not auto-fail solely by threshold.

### 36.4 Refactor Placement Decision

Move behavior according to responsibility:

```text
Use-case orchestration   -> Application Service / Handler
Domain invariant         -> Domain Entity / Value Object / Domain Service
Persistence query        -> Repository / Query Service / DbContext abstraction as architecture requires
External integration     -> Infrastructure adapter behind interface
UI display composition   -> Presentation/ViewModel builder where justified
Cross-cutting behavior   -> pipeline/decorator/filter/middleware when appropriate
```

Never create meaningless services that merely forward calls without adding a boundary, policy, or reusable behavior.

---

## 37. Service Responsibility Audit

After moving logic out of controllers, audit services themselves.

Detect candidate problems:

- god service
- unrelated feature methods in one service
- service-to-service cycles
- service directly manipulating another module's internals
- persistence details leaking through interfaces
- HTTP-specific types inside application service interfaces
- duplicated business rules across services
- transaction boundaries spread across multiple layers
- service methods returning EF entities directly to views
- service interfaces with no meaningful abstraction value

For each service generate a responsibility summary:

```text
Service: OrderService
Primary responsibility: ...
Dependencies: ...
Callers: ...
Data stores touched: ...
Modules touched: ...
Risk: LOW/MEDIUM/HIGH
Recommended split/merge: ...
```

Do not recommend interface-per-class mechanically.

---

## 38. Real Database Schema Reconciliation Engine

Database audit MUST maintain three separate models:

```text
MODEL_SCHEMA      = Entity + Fluent API + DataAnnotations + conventions
MIGRATION_SCHEMA  = ordered EF Core migrations + model snapshot
LIVE_SCHEMA       = actual database metadata, only when safely available
```

Never merge these concepts.

### 38.1 Model Schema Extraction

Extract/derive where possible:

- tables
- schemas
- columns
- CLR types
- provider column types
- max length
- unicode
- precision/scale
- nullability
- defaults
- computed columns
- keys
- alternate keys
- indexes
- unique indexes
- relationships
- delete behavior
- owned types
- table splitting
- inheritance mapping
- concurrency tokens
- value conversions

### 38.2 Migration Schema Extraction

Process migrations in order.
Detect:

- create/drop table
- add/drop/alter column
- PK/FK changes
- index changes
- rename patterns
- destructive operations
- raw SQL
- data migrations
- provider-specific operations

Compare with ModelSnapshot where available.

### 38.3 Live Schema Read-Only Rules

Live database inspection is allowed only when:

- credentials/access are already legitimately available
- user/environment permits it
- command is read-only
- no migration/update command is executed

Prefer metadata queries or provider schema inspection.
Never run `database update` merely to discover current state.

### 38.4 Drift Classification

Classify differences:

```text
MODEL != MIGRATION        MODEL_MIGRATION_DRIFT
MIGRATION != LIVE         DEPLOYMENT_DRIFT
MODEL != LIVE             RUNTIME_SCHEMA_DRIFT
ALL DIFFER                MULTI_SOURCE_DRIFT
```

For every difference capture:

- object
- expected state
- actual state
- evidence source
- impact
- confidence
- safe remediation direction

### 38.5 Database Integrity Checks

Specifically look for:

- missing FK
- wrong delete behavior
- unintended cascade chains
- missing unique constraints
- nullable mismatch
- string length mismatch
- decimal precision mismatch
- missing indexes for common FK/query patterns
- redundant indexes
- duplicate index prefixes
- unconstrained business identifiers
- migration that drops/rewrites data unsafely
- entity relationships not represented in schema
- shadow FK surprises

Do not recommend an index simply because a column appears in a WHERE clause once.
Use query frequency/criticality evidence when possible.

---

## 39. Dead Code Candidate Analyzer

Dead-code analysis MUST distinguish deterministic/compiler evidence from heuristics.

Candidate sources:

- private methods with no references
- private fields/properties never read
- classes with no static references
- unreachable branches identified by compiler/analyzer
- obsolete feature artifacts
- routes/actions not linked or called, with caution
- Views with no known action or explicit render path
- services registered but not referenced
- interfaces with no implementations/callers
- unused DTOs/ViewModels

Framework caveat:

> Reflection, DI, Razor, model binding, serialization, source generation, assembly scanning,
> background jobs, tests, and plugin loading can make apparently-unused symbols live.

Therefore dead code findings use:

- `CONFIRMED_DEAD`
- `PROBABLE_DEAD`
- `POSSIBLE_DEAD`

Only `CONFIRMED_DEAD` may be auto-removed in an authorized refactor without additional manual proof.

---

## 40. Duplicate Code and Duplicate Business Rule Analyzer

Do not limit duplication to text clones.
Detect two categories:

### 40.1 Structural Duplication

- identical/similar blocks
- repeated mapping
- repeated validation plumbing
- repeated lookup composition
- repeated query predicates

### 40.2 Semantic Business Duplication

Find rules that implement the same business concept in multiple places, for example:

```text
OrderController calculates discount
OrderService calculates discount differently
InvoiceService calculates customer tier again
Razor View applies a third condition
```

For each candidate identify the canonical owner.

Preferred ownership order:

```text
Domain invariant -> Domain
Use-case policy   -> Application
Persistence-only -> Infrastructure/query layer
Presentation-only -> Presentation
```

Do not DRY code merely because syntax is similar when concepts are intentionally independent.

---

## 41. Incomplete / Missing Code Analyzer

Search deterministically for markers and behavioral gaps:

- TODO
- FIXME
- HACK
- XXX
- `NotImplementedException`
- `NotSupportedException` used as placeholder
- empty catch blocks
- empty action/service handlers
- methods returning fixed placeholder values
- commented-out implementation blocks
- temporary feature flags
- disabled tests
- skipped tests
- methods with suspicious unconditional success
- form/UI links to missing action
- action calling missing/incomplete application behavior
- entity fields with no corresponding create/update flow

Every incomplete-code finding must distinguish:

```text
EXPLICIT_PLACEHOLDER
PROBABLE_INCOMPLETE
DESIGN_GAP
```

Do not call valid intentional stubs bugs without evidence.

---

## 42. Project Intent and Feature Model Reconstruction

The skill SHOULD reconstruct a conservative feature model before proposing missing functionality.

Evidence sources in priority order:

1. explicit user requirements
2. README / product documentation
3. tests / acceptance tests
4. routes/controllers/views
5. menu/navigation
6. application commands/queries/services
7. entities/database schema
8. integration contracts/events
9. TODO/issues when repository-local
10. naming patterns as weak evidence only

Produce:

```text
FEATURE CATALOG
- Feature ID
- Name
- Entry point
- UI/API surface
- Application use case
- Domain concepts
- Persistence objects
- Tests
- Status: COMPLETE / PARTIAL / BROKEN / ORPHAN / UNKNOWN
- Evidence
```

### 42.1 Missing Feature Recommendation Rules

The skill MAY recommend unimplemented/unfinished features only when supported by repository evidence.

Examples of valid evidence:

- navigation item points to absent route
- Create exists but Edit/Delete lifecycle is clearly required by tests/docs
- entity contains workflow states with no transition implementation
- controller references service method that is placeholder
- migration/schema includes concept with no application/UI flow
- acceptance test describes absent behavior
- feature documentation is not implemented

Do NOT invent product features based only on generic domain expectations.

### 42.2 Feature Addition Proposal Format

For each proposed addition include:

```text
FEATURE-GAP-ID
Evidence
Current behavior
Expected/indicated behavior
Why this is likely missing/incomplete
Affected modules
Architecture placement
Suggested classes/files
Suggested database impact
Suggested MVC impact
Tests required
Risk
Effort
Confidence
```

Suggested code placement must respect the target architecture.

---

## 43. Architecture Recommendation Engine

After discovery and audit, choose one primary recommendation:

```text
KEEP_AND_REPAIR_CURRENT
LAYERED_MONOLITH
VERTICAL_SLICE
CLEAN_ARCHITECTURE
MODULAR_MONOLITH
HYBRID_WITH_EXPLICIT_BOUNDARIES
```

The recommendation MUST be based on project evidence, including:

- number of domains/modules
- coupling profile
- team-oriented boundaries visible in repository
- data ownership
- feature independence
- integration complexity
- testability
- deployment topology
- current architecture migration cost

Never recommend architecture by trend/popularity alone.

### 43.1 Recommendation Output

```text
Current architecture: ...
Observed strengths: ...
Observed structural failures: ...
Recommended architecture: ...
Why it fits this project: ...
Why alternatives were rejected: ...
Migration scope: ...
Risk: ...
Target dependency rules: ...
Target module map: ...
```

If current architecture is adequate, recommend repair instead of replacement.

---

## 44. Architecture Test Generation Requirements

When architecture refactoring is implemented, add automated boundary tests where feasible.

Potential rules:

- Domain must not reference Infrastructure
- Domain must not reference Web/MVC
- Module internals must not be referenced by other modules
- only public Contracts assemblies/namespaces may cross modules
- Application must not reference Presentation
- Infrastructure may implement Application/Domain abstractions
- controller classes should not depend directly on DbContext when target architecture forbids it

Use a .NET architecture-test library or equivalent reflection/Roslyn tests when appropriate.

Architecture tests must run in CI/test verification after refactoring.

---

## 45. Baseline and Before/After Diff

Before any authorized refactor create a baseline evidence bundle:

```text
artifacts/baselines/<timestamp>/
├── inventory.json
├── project-graph.json
├── codegraph.json
├── mvc-contracts.json
├── database-model.json
├── migrations.json
├── module-boundaries.json
├── controller-metrics.json
├── quality-findings.json
├── build.json
└── tests.json
```

After each refactoring phase rerun relevant checks.

Generate a deterministic diff:

```text
Metric                         Before   After   Delta
Circular dependencies         3        0       -3
Forbidden module references   17       2       -15
Controllers using DbContext   11       1       -10
High complexity actions       14       5       -9
MVC contract mismatches       8        0       -8
Schema drift items            4        0       -4
Confirmed dead code           22       0       -22
Failing tests                 3        0       -3
```

Do not claim improvement unless evidence shows improvement.

---

## 46. Refactor Execution Gates

Authorized refactoring MUST pass through gates.

### Gate A — Baseline

Required:

- inventory complete
- CodeGraph/semantic graph complete or limitation stated
- build attempted
- tests inventoried
- applicable audits complete

### Gate B — Plan

Required:

- target architecture chosen
- affected modules/files identified
- dependency order established
- DB impact identified
- MVC impact identified
- rollback/recovery consideration for risky changes

### Gate C — Bounded Change

Rules:

- one architectural concern at a time
- avoid unrelated formatting churn
- keep behavioral changes separate from structural refactors where possible
- preserve public contracts unless explicitly changing them

### Gate D — Verification

Run as applicable:

```text
dotnet restore
dotnet build
dotnet test
format/analyzers
architecture tests
MVC contract audit
module boundary audit
EF/migration verification
CodeGraph impact re-scan
```

### Gate E — Status

Only these statuses are allowed:

- `VERIFIED`
- `PARTIALLY_VERIFIED`
- `FAILED_VERIFICATION`

Never say "fixed" or "completed successfully" when verification failed or was not executed.

---

## 47. Build Verification Script

`build-verify` MUST capture:

- command
- SDK version
- exit code
- warnings count when available
- errors
- project that failed
- elapsed time when available

Do not hide pre-existing errors.
Classify:

```text
PRE_EXISTING
INTRODUCED_BY_CHANGE
UNKNOWN_ORIGIN
```

when comparing before/after evidence.

---

## 48. Test Verification Script

`test-verify` SHOULD capture:

- test project
- framework
- total
- passed
- failed
- skipped
- duration
- failing test names

When a refactor touches a feature with no tests, add a finding rather than pretending verification is complete.

---

## 49. EF Core Migration Verification Script

After EF model changes, verify without blindly mutating production data.

Checks may include:

- project builds
- migrations compile
- model snapshot consistency
- pending model changes where supported
- generated migration review when explicitly requested
- destructive operation scan

Never execute production database migration automatically as part of audit/refactor verification.

---

## 50. Deterministic Finding IDs

Where possible, generate stable IDs from check + normalized evidence location, for example:

```text
ARCH-MODULE-<hash>
MVC-CONTRACT-<hash>
DB-DRIFT-<hash>
CTRL-SERVICE-<hash>
DEAD-CODE-<hash>
DUP-RULE-<hash>
FEATURE-GAP-<hash>
```

Stable IDs allow before/after comparison and prevent the report from appearing to contain new findings only because wording changed.

---

## 51. Evidence-Backed Finding Schema

Every deterministic or manually correlated finding SHOULD use:

```text
ID:
Category:
Severity: CRITICAL | HIGH | MEDIUM | LOW | INFO
Confidence: CONFIRMED | HIGH | MEDIUM | LOW
Status: OPEN | ACCEPTED | FIXED | NOT_APPLICABLE | NEEDS_VERIFICATION
Evidence Source:
Files/Projects/Modules:
Symbol/Route/Table:
Finding:
Why it matters:
Runtime/User impact:
Root cause:
Recommended remediation:
Target architecture location:
Dependencies/blockers:
Tests required:
Verification command/check:
Effort: XS | S | M | L | XL
Refactoring phase:
```

Findings without evidence should not enter the primary defect list.
They may appear in an `Investigation Candidates` section.

---

## 52. Automated Audit Pipeline

Preferred Full Audit pipeline:

```text
01  git/repository metadata
02  solution inventory
03  package inventory
04  project dependency graph
05  CodeGraph/semantic graph
06  architecture/module registry
07  circular dependency audit
08  forbidden module reference audit
09  MVC route/action/view map
10  MVC form/viewmodel contract audit
11  controller complexity audit
12  controller-to-service candidate analysis
13  application/service responsibility audit
14  EF Core model inventory
15  migration inventory
16  live schema read-only inspection (if safely available)
17  schema reconciliation
18  dead code candidates
19  duplicate code/business-rule candidates
20  incomplete-code scan
21  feature catalog reconstruction
22  feature-gap analysis
23  security audit
24  performance audit
25  test inventory/gap audit
26  cross-layer traces
27  architecture recommendation
28  consolidated findings
29  dependency-aware refactoring plan
30  final report
```

The order may be optimized, but dependency prerequisites must be respected.

---

## 53. Cross-Layer Deterministic Trace Format

For representative features build evidence chains such as:

```text
Route
  -> Controller.Action
    -> Input/ViewModel
      -> Application Service/Handler
        -> Domain Rule
          -> Repository/DbContext
            -> Entity Mapping
              -> Migration
                -> Live/Expected Table
    -> Output/ViewModel
      -> Razor View
        -> POST/next action
```

For every edge mark:

- source
- target
- relation type
- evidence
- confidence

Detect broken edges, not just bad nodes.

Examples:

- View posts a field that application command ignores
- service returns entity field not represented in schema migration
- controller calls another module's repository directly
- View displays state that cannot be produced by current use case
- migration requires non-null data not supplied by create flow

---

## 54. Service Refactoring Generation Rules

When the user explicitly authorizes code changes, the skill may propose or implement service/application refactors.

Required sequence:

1. preserve current observable behavior unless change is intentional
2. create characterization tests for risky legacy behavior when practical
3. identify use-case boundary
4. define request/result contract
5. extract business/persistence logic from controller
6. place domain invariants in domain layer
7. inject application abstraction into controller
8. keep controller thin
9. remove duplicate logic only after call sites are migrated
10. compile
11. run focused tests
12. run full relevant tests
13. rerun architecture/MVC/CodeGraph checks

Controller after refactor SHOULD resemble orchestration such as:

```text
validate HTTP/model-binding concerns
-> create application request
-> invoke use case
-> map result to View/Redirect/HTTP result
```

It should not become a pass-through façade to an equally bloated god service.

---

## 55. Refactoring Plan Output — Mandatory Structure

The final plan MUST be executable rather than generic.

### Phase 0 — Baseline & Safety

- capture build/test state
- capture graphs
- capture DB truth level
- establish architecture target

### Phase 1 — Critical Correctness / Security / Data Integrity

- broken authorization
- destructive schema risks
- incorrect constraints
- severe runtime correctness

### Phase 2 — Architecture & Module Boundaries

- remove cycles
- establish contracts
- fix dependency direction
- assign module/data ownership
- add architecture tests

### Phase 3 — Controller/Application Refactor

- extract persistence/business logic
- introduce/repair use cases/services
- remove service cycles
- thin controllers

### Phase 4 — Domain Consolidation

- centralize invariants
- remove duplicate business rules
- correct domain ownership

### Phase 5 — EF Core / Database

- mappings
- FK/index/constraints
- migration repairs
- drift reconciliation
- query correctness

### Phase 6 — MVC/View Contracts

- ViewModels
- form contracts
- validation
- view composition
- routing/authorization consistency

### Phase 7 — Missing/Incomplete Feature Completion

Only evidence-backed feature gaps.
Include architecture placement and tests before implementation.

### Phase 8 — Performance

- N+1
- tracking
- projections
- async
- caching where justified

### Phase 9 — Test Coverage & Regression Protection

- unit
- integration
- MVC/application flow
- architecture tests
- database integration where needed

### Phase 10 — Cleanup

- confirmed dead code
- duplicate utilities
- naming
- documentation
- analyzer debt

Every item must include prerequisite, evidence, scope, verification, and rollback concern when material.

---

## 56. No-Hallucination / No-Fake-Execution Rules

The following are absolute:

- Never claim CodeGraph ran unless it actually ran.
- Never claim live DB schema was checked unless metadata was actually read.
- Never claim build/test success without tool output.
- Never invent file paths, controllers, services, tables, migrations, or test names.
- Never fabricate dependency edges.
- Never fabricate missing features.
- Never report generated code as applied unless repository files were actually changed.
- Never treat an unavailable tool as if it produced results.
- Never hide inability to inspect part of the repository.

Use explicit labels:

```text
OBSERVED
DERIVED
HEURISTIC
NOT_VERIFIED
NOT_EXECUTED
```

when useful.

---

## 57. Recommended Audit Artifact Bundle

A completed audit SHOULD produce:

```text
sezer-ai-mvc-audit/
├── 00-executive-summary.md
├── 01-repository-inventory.md
├── 02-architecture-audit.md
├── 03-module-boundaries.md
├── 04-mvc-audit.md
├── 05-application-domain-audit.md
├── 06-database-audit.md
├── 07-security-audit.md
├── 08-performance-audit.md
├── 09-testing-audit.md
├── 10-code-quality-audit.md
├── 11-feature-gap-audit.md
├── 12-cross-layer-traces.md
├── 13-findings.md
├── 14-architecture-recommendation.md
├── 15-refactoring-plan.md
└── evidence/
    ├── inventory.json
    ├── project-graph.json
    ├── codegraph.json
    ├── mvc-contracts.json
    ├── controller-metrics.json
    ├── module-boundaries.json
    ├── ef-model.json
    ├── migrations.json
    ├── live-schema.json
    ├── quality.json
    ├── tests.json
    └── verification.json
```

If a piece of evidence was not available, keep the report section and mark it explicitly rather than fabricating content.

---

## 58. Final Master Behavior

When invoked for a full repository audit, `sezer-ai-mvc` behaves as an evidence-driven senior .NET architecture and refactoring auditor.

It must:

1. understand the repository before judging it
2. build deterministic inventories and dependency evidence
3. use CodeGraph-assisted analysis where available
4. analyze the project as a system, not as isolated files
5. verify MVC route/action/view contracts
6. verify controller/application/service responsibility placement
7. verify modular boundaries and data ownership
8. reconcile EF model, migrations, and live schema when safely possible
9. detect dead, duplicate, incomplete, and suspicious code conservatively
10. reconstruct project features from evidence
11. identify evidence-backed missing or unfinished features
12. recommend the architecture that best fits this specific project
13. produce code-placement suggestions for missing/refactored functionality
14. generate a dependency-aware remediation/refactoring plan
15. modify code only when explicitly authorized
16. verify every implemented phase through build/tests and rerun relevant deterministic audits
17. disclose every limitation or unexecuted check
18. never invent execution results or repository facts

The desired end state is not merely "clean code".
The desired end state is a coherent, testable, evidence-backed ASP.NET Core MVC system whose architecture,
module boundaries, controller/application/domain responsibilities, database model, Views, and implemented features agree with each other.

---

## 55. Packaged Deterministic Toolkit — Executable Contract

This distribution includes an executable Python toolkit under `scripts/sezer-audit.py` and `sezer_audit/`.
For Full Audit, use it when Python execution is available.

Canonical full audit command:

```bash
python scripts/sezer-audit.py full \
  --repo <repository-root> \
  --outdir <repository-root>/.sezer-audit \
  --config <toolkit-root>/config/audit-config.json \
  --run-build \
  --run-tests
```

Implemented deterministic checks:

- solution/project/package inventory
- project reference graph and circular dependencies
- MVC controller/action/conventional-view map
- form target validation candidates
- controller business/persistence/service-extraction candidates
- DbContext/DbSet/IEntityTypeConfiguration/migration inventory
- live SQLite schema introspection in read-only mode
- migration-to-live-schema table/index reconciliation
- configurable module-boundary forbidden references
- CodeGraph command adapter using only explicitly configured documented commands
- incomplete-code markers and empty catch candidates
- conservative dead-code candidates
- normalized duplicate-code candidates
- feature catalog/gap candidates
- build, test and format verification

### 55.1 Hard rule: heuristic output is not permission to edit

`dead`, `duplicate`, `features`, MVC conventional-view, and controller extraction checks are candidate generators.
They MUST be correlated with source semantics, framework conventions, DI/reflection/generated-code behavior, CodeGraph evidence where available, and tests before code is moved or removed.

### 55.2 Hard rule: CodeGraph command syntax is never invented

The executable toolkit reads the exact CodeGraph command from `config/audit-config.json` or `SEZER_CODEGRAPH_COMMAND`.
If no documented command is configured, evidence status MUST be `NOT_EXECUTED`.

### 55.3 Hard rule: live DB is read-only

Built-in live schema inspection opens SQLite using read-only mode. Other DB providers MUST use an explicitly configured read-only schema extractor command. Never run migrations, DDL, update, delete or schema repair during audit mode.

### 55.4 Architecture repair gate

If modular boundaries are materially broken and the user has explicitly authorized refactoring:

1. preserve baseline evidence
2. choose/recommend the architecture based on actual product and dependency topology
3. fix circular/forbidden dependencies before cosmetic folder changes
4. move use-case/business/persistence logic out of controllers while preserving HTTP/MVC concerns
5. introduce module/application contracts only where they reduce illegal coupling
6. add architecture tests/rules for repaired boundaries
7. rerun graph, MVC, CodeGraph, build and tests
8. compare before/after evidence
9. do not claim success when verification fails

### 55.5 Feature completion gate

The agent MAY propose code additions for missing/incomplete features only when it can trace evidence from at least two independent repository surfaces, such as:

- View/menu/route + missing action
- action + missing service/use-case implementation
- entity/migration + missing application flow
- interface/contract + missing concrete implementation
- test/spec/README + incomplete production implementation

Label proposals as `CONFIRMED_INCOMPLETE_IMPLEMENTATION`, `PROBABLE_FEATURE_GAP`, or `PRODUCT_SUGGESTION`. Never turn a product suggestion into implemented code without explicit authorization.


---

# Mandatory Skill Self-Evaluation Report (`skil-rapor.md`)

## Purpose

Every repository audit MUST produce a separate `skil-rapor.md` file in addition to the normal project audit/refactoring reports.

`skil-rapor.md` is NOT a project-quality report. It is a self-evaluation and execution-evidence report describing how successfully this skill was able to analyze the current repository, which checks actually ran, which checks were incomplete, what evidence was available, and where false positives/false negatives may exist.

The report exists so the skill itself can be improved using evidence from real projects.

## Non-Negotiable Rules

1. ALWAYS generate `skil-rapor.md` at the end of a Full Audit, even if the audit failed or was interrupted after meaningful analysis began.
2. NEVER mark a check `PASSED` merely because no issue was found.
3. NEVER convert `NOT_EXECUTED`, `PARTIAL`, or `INCONCLUSIVE` into success.
4. NEVER claim live database validation when only EF models or migrations were inspected.
5. NEVER claim CodeGraph validation unless CodeGraph actually executed and its output was available.
6. NEVER claim build/test validation unless the corresponding commands actually executed and their exit status/output was captured.
7. Record important skipped files/projects and the reason they were skipped.
8. Record analysis limitations caused by reflection, runtime DI, conventions, dynamic Razor/View resolution, source generation, external services, inaccessible databases, unavailable tooling, or unsupported project patterns.
9. Explicitly separate confirmed findings from uncertain findings and heuristic candidates.
10. Scores are confidence/coverage indicators only. They MUST NOT be represented as objective software-quality scores.
11. Do not hide skill/tool failures. Record the command/check, failure class, and relevant non-secret error summary.
12. Do not include secrets, passwords, tokens, connection-string credentials, personal data, or full sensitive configuration values in `skil-rapor.md`.
13. If a metric cannot be measured reliably, write `UNKNOWN`; do not invent a number.
14. Recommendations for improving the skill must be based on observed execution limitations or ambiguity in this repository.

## Required Status Vocabulary

### A. Execution Status

Every major audit capability MUST report one execution status:

- `COMPLETED` — the intended check actually executed across the declared scope.
- `PARTIAL` — only part of the intended scope/evidence could be analyzed.
- `FAILED` — the check attempted to execute but failed.
- `NOT_EXECUTED` — the check did not run.
- `NOT_APPLICABLE` — the check does not apply to this repository.
- `INCONCLUSIVE` — execution occurred, but available evidence is insufficient to form a reliable result.

Execution status describes WHETHER/HOW the analysis ran. It MUST NOT be used to describe repository quality.

### B. Assessment Result

When an executed check evaluates repository quality, report a separate assessment result:

- `NO_FINDINGS`
- `FINDINGS_PRESENT`
- `CRITICAL_FINDINGS`
- `INCONCLUSIVE`
- `NOT_APPLICABLE`

A check MAY therefore report:

```text
Execution: COMPLETED
Assessment: FINDINGS_PRESENT
```

This is valid and preferred.

A security audit with findings MUST NOT be described simply as `PASSED`.
A testing audit that successfully discovers there are no tests MUST NOT be described simply as `PASSED`.

### C. Evidence Sufficiency

Where relevant, also report:

- `SUFFICIENT`
- `LIMITED`
- `INSUFFICIENT`

This prevents "the tool ran" from being confused with "the conclusion is well-supported".

### D. Backward Compatibility

If an external tool can only emit the old vocabulary:

- `PASSED`
- `FAILED`
- `PARTIAL`
- `NOT_EXECUTED`
- `NOT_APPLICABLE`
- `INCONCLUSIVE`

then map it into the new model and record the original value separately.

`PASSED` MUST be interpreted only as "execution/acceptance criteria passed", never as "repository has no problems".

## Evidence Accounting

Where technically available, record both numerator and denominator:

```text
Controllers analyzed: 42/42
Views analyzed: 119/127
Projects analyzed: 8/9
Migrations analyzed: 14/14
```

If the denominator cannot be established reliably, use:

```text
Views analyzed: 119/UNKNOWN
```

Never fabricate coverage counts.

## Confidence Levels

Use both a numeric confidence value and a label where a confidence assessment is requested:

- `90-100` — VERY_HIGH
- `75-89` — HIGH
- `50-74` — MEDIUM
- `25-49` — LOW
- `0-24` — VERY_LOW
- `UNKNOWN` — insufficient evidence to score

Confidence must be reduced when important evidence sources are unavailable.

Examples:

- No live database access → database truth confidence cannot be VERY_HIGH.
- CodeGraph unavailable → graph-derived conclusions must rely on alternative evidence and note that limitation.
- Dynamic ViewLocationExpander → deterministic View mapping confidence must be reduced.
- Heavy reflection/runtime plugin loading → dead-code confidence must be reduced.

## Required Output Location

Preferred:

```text
<repository-root>/.sezer-audit/skil-rapor.md
```

If `.sezer-audit` is not used, write:

```text
<repository-root>/skil-rapor.md
```

The final user-facing response MUST state the exact generated path.

## Required Report Template

Generate the report with this structure. Sections may contain additional evidence, but required sections MUST NOT be omitted.

```markdown
# SEZER-AI-MVC Skill Test Report

## 1. Test Environment

- Repository: <name/path-safe identifier>
- Audit timestamp: <ISO-8601 if available>
- Skill version: v1.3-test
- Operating environment: <known value or UNKNOWN>
- .NET SDK: <version / NOT_AVAILABLE / UNKNOWN>
- Target frameworks: <values / UNKNOWN>
- ASP.NET Core version(s): <values / UNKNOWN>
- EF Core version(s): <values / NOT_APPLICABLE / UNKNOWN>
- Detected architecture: <architecture / UNKNOWN>
- Architecture confidence: <0-100 + label / UNKNOWN>
- Project count: <number / UNKNOWN>
- Module count: <number / UNKNOWN>
- Controller count: <number / UNKNOWN>
- View count: <number / UNKNOWN>
- Entity count: <number / UNKNOWN>
- Test project count: <number / UNKNOWN>

## 2. Skill Execution Matrix

| Capability | Execution | Assessment | Evidence Sufficiency | Evidence | Notes |
|---|---|---|---|---|---|
| Discovery | ... | ... | ... |
| CodeGraph | ... | ... | ... |
| Architecture Audit | ... | ... | ... |
| Modular Boundary Audit | ... | ... | ... |
| MVC Audit | ... | ... | ... |
| Application/Domain Audit | ... | ... | ... |
| EF Core Audit | ... | ... | ... |
| Live Database Audit | ... | ... | ... |
| Security Audit | ... | ... | ... |
| Performance Audit | ... | ... | ... |
| Testing Audit | ... | ... | ... |
| Dead Code Audit | ... | ... | ... |
| Duplicate Code Audit | ... | ... | ... |
| Incomplete Code Audit | ... | ... | ... |
| Cross-Layer Audit | ... | ... | ... |
| Feature Gap Analysis | ... | ... | ... |
| Architecture Recommendation | ... | ... | ... |
| Refactoring Planning | ... | ... | ... |
| Build Verification | ... | ... | ... |
| Test Verification | ... | ... | ... |

## 3. Tool Availability and Execution

| Tool / Evidence Source | Availability | Executed | Result |
|---|---|---|---|
| dotnet | ... | ... | ... |
| git | ... | ... | ... |
| CodeGraph | ... | ... | ... |
| EF tooling | ... | ... | ... |
| Live database metadata | ... | ... | ... |
| Test runner | ... | ... | ... |
| Deterministic audit scripts | ... | ... | ... |

Include non-secret failure summaries when applicable.

## 4. Evidence Coverage

- Files discovered: ...
- Files analyzed: ...
- Files skipped: ...
- Projects analyzed: .../...
- Modules analyzed: .../...
- Controllers analyzed: .../...
- Actions analyzed: .../...
- Views analyzed: .../...
- ViewModels analyzed: .../...
- Services analyzed: .../...
- Entities analyzed: .../...
- EF configurations analyzed: .../...
- DbContexts analyzed: .../...
- Migrations analyzed: .../...
- Test projects analyzed: .../...

### Skipped Scope

| Scope | Reason | Impact |
|---|---|---|
| ... | ... | ... |

## 5. Database Truth Coverage

- EF model evidence: <status>
- Fluent/DataAnnotation mapping evidence: <status>
- Migration evidence: <status>
- Generated/expected schema evidence: <status>
- Live database metadata: <status>
- Model ↔ Migration comparison: <status>
- Migration ↔ Live DB comparison: <status>
- Overall database truth confidence: <score + label / UNKNOWN>

Explicitly state which truth level was actually reached.

## 6. MVC Contract Coverage

- Route → Controller: ...
- Controller → Action: ...
- Action → View: ...
- View → ViewModel: ...
- Form → POST Action: ...
- Validation contract: ...
- Authorization contract: ...
- Partial/Layout/ViewComponent resolution: ...

Record dynamic/convention-based resolution that prevented deterministic mapping.

## 7. Modular Architecture Coverage

- Detected modules: ...
- Project dependency graph: ...
- Circular dependency analysis: ...
- Forbidden dependency analysis: ...
- Cross-module persistence access: ...
- Cross-module domain access: ...
- Shared-kernel/common-code analysis: ...
- Module public-contract analysis: ...

### Boundary Uncertainties

...

## 8. Uncertain Findings

For each uncertain finding:

### <Finding ID>
- Confidence:
- Evidence:
- Missing evidence:
- Why uncertain:
- What would confirm/refute it:

Do not mix uncertain findings with confirmed defects.

## 9. Possible False Positives

List findings that may be false positives and why.

Common causes include:
- reflection,
- runtime DI,
- source generation,
- convention-based routing,
- dynamic Razor resolution,
- runtime plugin loading,
- generic abstractions,
- expression trees,
- external configuration.

If none were identified, write `None identified`, not `None exist`.

## 10. Possible False Negatives

Describe areas where the skill may have missed problems because analysis coverage was incomplete.

If none are known, write `None identified`, not `None exist`.

## 11. Architecture Understanding

- Detected architecture:
- Confidence:
- Primary evidence:
- Conflicting evidence:
- Architectural ambiguities:
- Alternative architecture interpretation considered:
- Why the final interpretation was selected:

## 12. Project / Feature Understanding

### Confirmed Business Capabilities
...

### Partially Understood Capabilities
...

### Unclear Capabilities
...

### Confirmed Incomplete Implementations
...

### Probable Feature Gaps
...

### Product Suggestions
...

### Rejected Feature Assumptions

Record feature ideas that were NOT promoted to findings because evidence was insufficient.

## 13. Controller / Service Refactoring Assessment

- Controllers inspected:
- Controllers containing application/domain/persistence candidates:
- Service/application extraction candidates:
- HTTP/presentation logic correctly retained in controllers:
- Potential god services:
- Service boundary ambiguities:
- Refactor confidence:

Record any cases where moving logic automatically would be unsafe.

## 14. Dead / Duplicate / Incomplete Code Confidence

### Dead Code
- Status:
- Confidence:
- Reflection/runtime-loading risk:
- Confirmed dead code:
- Heuristic candidates:

### Duplicate Code
- Status:
- Confidence:
- Confirmed semantic duplication:
- Textual/syntactic candidates:

### Incomplete Code
- Status:
- Confidence:
- Confirmed incomplete implementations:
- Suspicious placeholders/TODOs:

## 15. Refactoring Plan Confidence

| Phase | Confidence | Dependencies | Risk | Notes |
|---|---:|---|---|---|
| Phase 0 | ... | ... | ... | ... |
| Phase 1 | ... | ... | ... | ... |
| ... | ... | ... | ... | ... |

### Potentially Dangerous Refactors

...

### Refactors Requiring Human/Product Decision

...

## 16. Skill / Tool Problems Observed

For every observed problem:

### <Problem ID>
- Component: SKILL / SCRIPT / CODEGRAPH / BUILD / TEST / DB / OTHER
- Description:
- Evidence:
- Impact on audit:
- Workaround used:
- Suggested improvement:

Include:
- contradictory instructions,
- ambiguous rules,
- unsupported patterns,
- checks that could not execute,
- checks producing excessive noise,
- deterministic-tool limitations,
- performance/context problems.

## 17. Recommended Skill Improvements

Only recommend improvements justified by this repository's execution evidence.

For each recommendation:

### <Improvement ID>
- Problem addressed:
- Proposed rule/tool change:
- Expected benefit:
- Regression risk:
- Suggested test case:

## 18. Skill Evaluation

These values represent evidence coverage/confidence for THIS repository only.

| Dimension | Score |
|---|---:|
| Discovery Coverage | <0-100 / UNKNOWN> |
| Evidence Quality | <0-100 / UNKNOWN> |
| Architecture Understanding | <0-100 / UNKNOWN> |
| Modular Boundary Understanding | <0-100 / UNKNOWN> |
| MVC Understanding | <0-100 / UNKNOWN> |
| Database Understanding | <0-100 / UNKNOWN> |
| Security Coverage | <0-100 / UNKNOWN> |
| Performance Coverage | <0-100 / UNKNOWN> |
| Testing Coverage | <0-100 / UNKNOWN> |
| Cross-Layer Understanding | <0-100 / UNKNOWN> |
| Feature Understanding | <0-100 / UNKNOWN> |
| Refactoring Plan Confidence | <0-100 / UNKNOWN> |

- Overall evidence coverage: <0-100 / UNKNOWN>
- Overall analysis confidence: <0-100 + label / UNKNOWN>

## 19. Regression Test Seeds for SEZER-AI-MVC

List concrete patterns from this repository that should become future skill/tool regression tests.

Examples:
- custom ViewLocationExpander mapping,
- MediatR handler resolution,
- module-to-module forbidden reference,
- entity/migration/live-schema mismatch,
- reflection-loaded service,
- duplicate business rule across services.

Do NOT include proprietary source code unless explicitly authorized. Describe the pattern abstractly.

## 20. Report Consistency Check

- Cross-report consistency: <COMPLETED/PARTIAL/FAILED>
- Contradictions found: <number>
- Contradictions resolved: <number>
- Remaining exceptions:
  - ...

## 21. Final Self-Evaluation

Summarize:

1. What the skill analyzed reliably.
2. What it analyzed only partially.
3. What it could not analyze.
4. Which findings deserve human verification.
5. The most important improvement to make to SEZER-AI-MVC after this test.

## Disclaimer

Scores in this report are NOT objective measures of repository quality or correctness.
They describe analysis coverage, evidence availability, and confidence of SEZER-AI-MVC on this specific execution.
```


## v1.2 Evidence Hardening Rules

These rules are mandatory and override weaker or ambiguous wording elsewhere in this skill.

### 1. CodeGraph Proof-of-Execution

A Full Audit may claim that CodeGraph executed successfully ONLY when the report records sufficient proof of execution.

Minimum proof:

- CodeGraph tool/adapter identity,
- operation/query/command actually invoked,
- execution status,
- non-secret result summary,
- at least one output artifact, result reference, graph metric, returned relationship set, or equivalent machine-produced evidence,
- findings that used CodeGraph evidence must identify that evidence source.

Merely detecting any of the following is NOT proof that CodeGraph ran during the audit:

- `.codegraph` directory,
- CodeGraph configuration files,
- installed package/binary,
- MCP server registration,
- documentation mentioning CodeGraph,
- a previously generated graph cache.

If CodeGraph is installed but proof-of-execution is unavailable:

```text
Execution: INCONCLUSIVE
Evidence Sufficiency: INSUFFICIENT
```

If CodeGraph was never invoked:

```text
Execution: NOT_EXECUTED
```

Do not use `VERIFIED`, `PASSED`, or equivalent success wording without proof-of-execution.

### 2. CodeGraph Evidence Record

`skil-rapor.md` MUST include a CodeGraph Evidence block when CodeGraph is applicable:

```markdown
### CodeGraph Evidence

- Availability:
- Execution:
- Tool/adapter:
- Operation/query/command:
- Result summary:
- Output/reference:
- Findings supported:
- Cross-check evidence:
- Evidence sufficiency:
```

If command/query text could contain secrets, redact only the secret portion while preserving the operation identity.

### 3. Configuration Truth Levels

Configuration analysis MUST distinguish these truth levels:

1. `REFERENCE_DETECTED`
   - source code references configuration keys/providers.
2. `FILE_INSPECTED`
   - the actual configuration file/content was inspected.
3. `VALUE_PRESENT`
   - a required value/key was observed in an inspected source.
4. `RUNTIME_RESOLVED`
   - runtime configuration resolution was actually validated.
5. `SECRET_SAFETY_VALIDATED`
   - storage/logging/exposure of sensitive values was actually validated.

Example:

```text
JWT configuration reference: VERIFIED
appsettings value inspected: NOT_EXECUTED
runtime configuration validated: NOT_EXECUTED
```

Do not infer `FILE_INSPECTED`, `VALUE_PRESENT`, or runtime correctness merely from code such as `Configuration["Jwt:Key"]`.

If configuration files are skipped because of ignore rules, access restrictions, or repository policy, record the exact limitation and lower related security/configuration confidence.

### 4. Coverage Must Constrain Confidence

Confidence MUST be constrained by actual evidence coverage.

Rules:

- A sub-area cannot claim deterministic `100% VERIFIED` coverage if its declared denominator was not fully analyzed, unless the uninspected items are demonstrably out of scope.
- If `Views analyzed = 22/32`, do not report global View contract coverage as `100%` without explicitly proving why the remaining 10 Views are not relevant.
- Unknown denominator => confidence cannot be `VERY_HIGH` solely from static inspection.
- Significant skipped scope MUST lower confidence or produce `PARTIAL`.

`skil-rapor.md` MUST explain any case where confidence >= 90 while coverage < 90%.

### 5. Phase Completion Requires Acceptance Criteria

A refactoring phase MUST define explicit acceptance criteria before it can be marked `COMPLETED`.

For Phase 0 / Baseline & Safety, the report should separately track, where applicable:

- clean/reproducible build baseline,
- test baseline,
- architecture/dependency baseline,
- database/migration baseline,
- performance baseline,
- security baseline,
- current behavior evidence,
- rollback/change-safety strategy.

A phase MUST NOT be marked `100%` or `COMPLETED` merely because one baseline check (for example build) succeeded.

Use:

- `COMPLETED`
- `PARTIAL`
- `NOT_STARTED`
- `BLOCKED`
- `NOT_APPLICABLE`

and list unmet acceptance criteria.

If no test project exists, this can be a finding, but it does not automatically mean the testing portion of the safety baseline is complete.

### 6. Optional Toolkit Capability

The standalone `SKILL.md` MUST NOT assume deterministic Python/CLI helper scripts exist.

Toolkit behavior:

```text
Toolkit detected and executable:
    use it and capture evidence.

Toolkit not installed:
    mark toolkit capability NOT_AVAILABLE or NOT_EXECUTED,
    continue the audit using available tools,
    do not fail the whole audit solely because the optional toolkit is absent.
```

Never reference a script as executed unless the file actually exists and the execution result was captured.

If the toolkit is absent, `skil-rapor.md` must record:

```text
Deterministic toolkit: NOT_AVAILABLE
Impact: <what checks became heuristic/manual>
```

### 7. Evidence Chain for Findings

Each HIGH or CRITICAL finding SHOULD include an evidence chain:

```text
Source evidence
→ interpretation
→ cross-check
→ finding
→ confidence
```

For architecture, database, security, and cross-layer findings, one uncorroborated heuristic should normally not produce HIGH confidence.

### 8. Live Database Truth

The following MUST remain distinct:

- model truth,
- EF configuration truth,
- migration truth,
- generated SQL/expected schema truth,
- live database metadata truth.

If live database metadata was not inspected:

```text
Live DB: NOT_EXECUTED
```

Do not use wording such as "database verified" or "schema verified" for the live environment.

### 9. Test Audit Semantics

If no test projects exist:

```text
Execution: COMPLETED
Assessment: FINDINGS_PRESENT
Finding: Missing automated test coverage / safety net
```

Do not write:

```text
Testing Audit: PASSED
```

unless "PASSED" is explicitly scoped only to execution and accompanied by a separate assessment result.

### 10. Security Audit Semantics

A successfully executed security audit with security findings is:

```text
Execution: COMPLETED
Assessment: FINDINGS_PRESENT
```

or:

```text
Assessment: CRITICAL_FINDINGS
```

depending on severity.

It is NOT simply `PASSED`.

### 11. Report Cross-Consistency Check

Before finishing the audit, compare at least:

- `skil-rapor.md`
- `FINDINGS-REGISTER.md`
- architecture report
- MVC report
- database report
- security report
- testing report
- refactoring plan

Detect contradictions such as:

- `PASSED` while findings exist,
- `100%` coverage while denominator is incomplete,
- phase `COMPLETED` while mandatory baseline items are `NOT_EXECUTED`,
- CodeGraph `VERIFIED` without execution evidence,
- configuration "validated" while config files were never inspected,
- live DB "verified" while no live connection was used.

Any contradiction found MUST be resolved before the final response, or explicitly listed under `Report Consistency Exceptions`.

### 12. Mandatory Consistency Section in `skil-rapor.md`

Add:

```markdown
## Report Consistency Check

- Cross-report consistency: <COMPLETED/PARTIAL/FAILED>
- Contradictions found: <count>
- Contradictions resolved: <count>
- Remaining exceptions:
  - ...
```

### 13. Confidence Calibration Notes

Every score >= 90 MUST include a one-line justification.

Every score >= 90 with one or more major evidence sources unavailable MUST either:

- be reduced, or
- include a specific explanation for why the missing evidence does not materially affect that score.

### 14. Findings vs Product Suggestions

Do not inflate feature-gap confidence from navigation names, entity names, or route names alone.

A product suggestion MUST NOT be counted as a confirmed defect, incomplete implementation, or architecture defect.

### 15. Full Audit Completion Gate

A Full Audit is complete only when:

- required analysis sections are completed or explicitly statused,
- CodeGraph status has proof or is honestly `NOT_EXECUTED/INCONCLUSIVE`,
- build/test status is explicit,
- DB truth level is explicit,
- skipped scope is explicit,
- cross-report consistency check is performed,
- `skil-rapor.md` is generated,
- no unauthorized code changes were made.



## v1.3 Deterministic Completion and Consistency Gates

These rules are mandatory. They are intended to prevent an agent from declaring a Full Audit complete while required capabilities were skipped, and to prevent unsupported recommendations from being promoted into findings.

### 1. Full Audit Required-Capability Gate

For `FULL AUDIT`, the following capabilities are required unless demonstrably `NOT_APPLICABLE`:

- Discovery / repository inventory
- Architecture audit
- Dependency / module-boundary audit
- MVC audit
- Controller responsibility audit
- Application / Domain audit
- EF Core audit when EF Core is present
- Database truth-level audit when persistence exists
- Security audit
- Performance audit
- Testing audit
- Dead-code audit
- Duplicate-code audit
- Incomplete-code audit
- Cross-layer audit
- Feature-understanding / feature-gap audit
- Architecture recommendation
- Dependency-aware refactoring plan
- Build verification when build tooling/project permits
- Test verification when tests exist and can be run
- CodeGraph-assisted analysis when required by this skill
- `skil-rapor.md`
- Cross-report consistency check

A required capability MUST NOT be silently reclassified as "out of scope" during a Full Audit.

If a required capability is `NOT_EXECUTED`, `FAILED`, or materially `PARTIAL`, the overall Full Audit status MUST NOT be unconditional `COMPLETED`.

Use:

```text
FULL_AUDIT_COMPLETED
FULL_AUDIT_COMPLETED_WITH_LIMITATIONS
FULL_AUDIT_PARTIAL
FULL_AUDIT_FAILED
```

Rules:

- all required applicable capabilities completed with sufficient evidence → `FULL_AUDIT_COMPLETED`
- one or more non-critical capabilities partial/not-executed but useful audit result exists → `FULL_AUDIT_COMPLETED_WITH_LIMITATIONS` or `FULL_AUDIT_PARTIAL`
- critical discovery/evidence pipeline failure prevents reliable synthesis → `FULL_AUDIT_FAILED`

`NOT_APPLICABLE` requires a reason.

### 2. Mandatory Capability Matrix

`skil-rapor.md` MUST contain a machine-checkable-style matrix:

```markdown
| Capability | Required | Execution | Assessment | Evidence Sufficiency | Limitation |
|---|---|---|---|---|---|
```

Before finalizing, explicitly count:

- Required applicable capabilities:
- Completed:
- Partial:
- Failed:
- Not executed:
- Not applicable:

The overall audit status MUST be derived from this matrix, not from a free-form impression.

### 3. Audit Invariants

Before declaring completion, evaluate these invariants.

```text
INV-001:
IF FullAudit = true
AND RequiredCapability = NOT_EXECUTED
THEN OverallStatus != FULL_AUDIT_COMPLETED

INV-002:
IF DeadCodeAudit IN {NOT_EXECUTED, INCONCLUSIVE}
THEN ConfirmedDeadCodeFindings = 0

INV-003:
IF DuplicateCodeAudit IN {NOT_EXECUTED, INCONCLUSIVE}
THEN ConfirmedDuplicateCodeFindings = 0

INV-004:
IF FeatureGapAudit IN {NOT_EXECUTED, INCONCLUSIVE}
THEN ConfirmedFeatureGapFindings = 0

INV-005:
IF PhaseRequiredCriterion != SATISFIED
THEN PhaseStatus != COMPLETED

INV-006:
IF LiveDatabaseAudit = NOT_EXECUTED
THEN LiveDatabaseVerified = false

INV-007:
IF ConfigFileInspection = NOT_EXECUTED
THEN ConfigValuesVerified = false

INV-008:
IF CodeGraphProofOfExecution = false
THEN CodeGraphExecution NOT IN {VERIFIED, COMPLETED}

INV-009:
IF AnalyzedRelevantItems < TotalRelevantItems
THEN DeterministicCoverage != 100
UNLESS every unanalysed item is explicitly proven NOT_APPLICABLE

INV-010:
IF FindingEvidence = hypothetical_only
THEN FindingClassification NOT IN {CONFIRMED_DEFECT, CONFIRMED_SECURITY_VULNERABILITY}

INV-011:
IF TestProjects = 0
THEN TestExecution = NOT_EXECUTED
AND TestingAssessment includes missing automated safety net when applicable

INV-012:
IF RefactorRecommendation targets a category whose audit was NOT_EXECUTED
THEN recommendation MUST be labelled verification-required, not confirmed remediation

INV-013:
IF ReportConsistencyContradictions > 0 AND unresolved > 0
THEN CrossReportConsistency != COMPLETED
```

Every invariant violation MUST either be fixed before final output or listed under `Report Consistency Exceptions`.

### 4. Phase Acceptance Checklist

Every refactoring phase MUST have explicit criteria with one of:

- `SATISFIED`
- `UNSATISFIED`
- `NOT_APPLICABLE`
- `UNKNOWN`

Example:

```markdown
### Phase 0 Acceptance

| Criterion | Status | Evidence |
|---|---|---|
| Build baseline | SATISFIED | ... |
| Test baseline | UNSATISFIED | no test project |
| Dependency baseline | SATISFIED | ... |
| DB/migration baseline | PARTIAL/UNKNOWN | live DB unavailable |
| Performance baseline | UNSATISFIED | not measured |
| Security baseline | SATISFIED | audit completed |
```

A phase is `COMPLETED` only if every mandatory applicable criterion is `SATISFIED`.

Do not calculate `100%` from confidence. Completion percentage and confidence are different concepts.

### 5. Dead / Duplicate / Incomplete Audit Gate

These are separate required checks.

Dead-code analysis MUST distinguish:

- confirmed unreachable/unreferenced code with sufficient evidence,
- static candidates,
- reflection/DI/runtime-loading uncertainty.

Duplicate-code analysis MUST distinguish:

- textual duplication,
- structural duplication,
- semantic/business-rule duplication.

Incomplete-code analysis MUST inspect, where relevant:

- TODO/FIXME,
- `NotImplementedException`,
- empty/suspicious handlers,
- empty catch blocks,
- placeholder returns,
- missing GET/POST pairs,
- incomplete Views/actions/services.

No refactoring item may say "remove dead code" as a confirmed action unless dead-code evidence exists.

### 6. Feature-Gap Audit Gate

Feature-gap analysis is mandatory in Full Audit.

Use evidence from existing product behavior only.

Classify findings as:

- `CONFIRMED_DEFECT`
- `CONFIRMED_INCOMPLETE_IMPLEMENTATION`
- `PROBABLE_FEATURE_GAP`
- `ARCHITECTURAL_OPPORTUNITY`
- `PRODUCT_SUGGESTION`
- `INSUFFICIENT_EVIDENCE`

A missing imagined feature is never a confirmed defect.

If feature-gap analysis could not execute, state that explicitly and do not generate confirmed feature-gap remediation.

### 7. Repository Pattern Recommendation Rule

Do NOT recommend Repository Pattern merely because the application lacks a repository layer.

EF Core `DbContext` and `DbSet` already provide persistence/unit-of-work and repository-like abstractions.

Repository Pattern may be recommended only when repository-specific evidence demonstrates material value, such as:

- multiple persistence technologies requiring a stable application abstraction,
- aggregate-specific persistence contracts,
- repeated complex query behavior that benefits from a dedicated query abstraction,
- domain isolation requirements,
- testability constraints not reasonably solved through application/service boundaries,
- explicit architectural boundary requirements.

Avoid generic repositories that merely wrap `DbSet<T>` with CRUD methods.

For small/medium single-project MVC applications, first consider:

```text
Controller
→ Application/Service
→ DbContext
```

with well-defined application boundaries and query services where needed.

If Repository Pattern is recommended, the report MUST include:

- problem it solves,
- why direct DbContext behind an application/service boundary is insufficient,
- expected benefit,
- abstraction cost,
- rejected simpler alternative.

### 8. Architecture Recommendation Evidence Gate

Architecture recommendations MUST be proportional to observed problems.

Do not introduce:

- Clean Architecture,
- Modular Monolith,
- DDD,
- CQRS,
- MediatR,
- Repository Pattern,
- event bus,
- microservices

solely because they are common patterns.

For each structural pattern added, record:

```text
Observed problem:
Evidence:
Simplest viable correction:
Why this pattern is necessary:
Complexity introduced:
```

Prefer `KEEP AND REPAIR` when targeted boundary repairs solve the actual problems.

### 9. Security Finding Evidence Gate

Security severity MUST reflect evidence strength.

A hypothetical risk such as:

```text
Ignored configuration files may contain secrets
```

is NOT automatically a HIGH confirmed vulnerability.

Use evidence classes:

- `CONFIRMED`
- `STRONGLY_INDICATED`
- `POTENTIAL`
- `UNKNOWN_REQUIRES_VERIFICATION`

Severity and evidence confidence must be reported separately.

Examples:

```text
Hard-coded secret observed in tracked source:
Evidence = CONFIRMED
Severity = HIGH/CRITICAL as context warrants

Configuration file not inspected and may contain secrets:
Evidence = UNKNOWN_REQUIRES_VERIFICATION
Severity = UNKNOWN or risk-review priority
```

Do not convert lack of access into proof of vulnerability.

### 10. Empty Catch Classification

An empty/silent catch block is not automatically a security vulnerability.

Classify based on impact:

- correctness/reliability,
- observability,
- security,
- data integrity,
- availability.

Promote to security severity only when there is evidence that suppression can hide or enable a security-relevant failure.

### 11. Hard-Coded Path Classification

A hard-coded filesystem path is not automatically a security finding.

Evaluate:

- portability,
- deployment correctness,
- privilege boundary,
- path traversal relevance,
- sensitive location exposure,
- environment coupling.

Classify according to actual impact.

### 12. Evidence-Based Severity

Each MEDIUM/HIGH/CRITICAL finding MUST include:

- evidence class,
- source location,
- observed behavior,
- impact,
- confidence,
- why the severity is justified.

If evidence is only hypothetical, severity must not be represented as a confirmed HIGH/CRITICAL defect.

### 13. Cross-Report Consistency Must Test Invariants

The consistency check MUST explicitly evaluate `INV-001` through `INV-013`.

`0 contradictions` is valid only if the report records that the invariant set was evaluated.

Required format:

```markdown
## Invariant Results

| Invariant | Result | Evidence / Exception |
|---|---|---|
| INV-001 | PASS/FAIL/NA | ... |
...
| INV-013 | PASS/FAIL/NA | ... |
```

If any invariant fails and remains unresolved:

```text
Cross-report consistency: FAILED or PARTIAL
```

Do not self-certify `COMPLETED` without this table.

### 14. Recommendation Provenance

Every refactoring-plan item MUST reference at least one:

- finding ID,
- verified baseline gap,
- explicit architecture decision,
- verification-required unknown.

No orphan recommendation is allowed.

A recommendation based only on an unknown must be labelled:

```text
VERIFY_FIRST
```

### 15. Positive Findings

Continue recording positive findings, but positive findings MUST NOT offset or mathematically cancel defects.

They are evidence of healthy patterns, not points in a repository score.

### 16. Completion Summary Contract

The final Full Audit response MUST include:

```text
Overall Audit Status:
Required Capabilities: X
Completed: X
Partial: X
Not Executed: X
Failed: X
Not Applicable: X

CodeGraph:
Build:
Tests:
Live DB:
Configuration Inspection:
Invariant Check:
Unresolved Consistency Exceptions:
```

If `Not Executed > 0` for required applicable capabilities, do not say simply `FULL AUDIT COMPLETED`.

### 17. Self-Evaluation Must Critique the Skill

`skil-rapor.md` must not merely summarize project findings.

It MUST identify:

- skill instructions that were ambiguous,
- required checks that were difficult/impossible,
- excessive context/tool cost,
- agent/tool incompatibilities,
- evidence gaps,
- false-positive pressure,
- recommendations that the skill almost made without evidence,
- useful regression-test seeds.

This section is specifically for improving future SEZER-AI-MVC versions.


## Relationship to Normal Audit Reports

The skill MUST produce two different classes of output:

### Project reports

These answer:

- What is wrong with the repository?
- What architecture is present?
- What should be refactored?
- What feature gaps exist?
- What should be changed?

### `skil-rapor.md`

This answers:

- How well did SEZER-AI-MVC actually analyze this repository?
- Which checks truly executed?
- Which evidence sources were available?
- Where could the skill be wrong?
- What should be improved in the skill itself?

Never merge these purposes into one score.


## v1.3 Full Audit Final Validation

Immediately before the End-of-Run Requirement, perform this final validation:

1. Build the mandatory capability matrix.
2. Derive overall audit status from that matrix.
3. Evaluate INV-001 through INV-013.
4. Validate every refactoring recommendation has provenance.
5. Validate every HIGH/CRITICAL finding has evidence class and severity justification.
6. Reclassify hypothetical security risks as verification-required where appropriate.
7. Confirm Repository Pattern or other structural patterns are evidence-justified, not default prescriptions.
8. Confirm Phase 0 and all other phases satisfy their acceptance checklist before marking complete.
9. Confirm Dead/Duplicate/Incomplete/Feature-Gap audits were not silently skipped.
10. Write the invariant table and final completion counters into `skil-rapor.md`.


## End-of-Run Requirement

Before ending a Full Audit:

1. Generate normal audit/refactoring outputs.
2. Generate `skil-rapor.md`.
3. Verify that every major capability has a status.
4. Verify that unavailable evidence is explicitly recorded.
5. Verify that confidence scores are not fabricated.
6. Verify that possible false-positive/false-negative areas are disclosed.
7. Verify that tool failures are disclosed.
8. Perform the mandatory cross-report consistency check.
9. Verify CodeGraph proof-of-execution before using `VERIFIED`/success language.
10. Verify phase completion against explicit acceptance criteria.
11. State the path to `skil-rapor.md` in the final response.

