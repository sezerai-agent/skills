# 🧠 SEZER AI MVC

### Evidence-Driven ASP.NET Core MVC Audit & Refactoring Skill

An advanced AI skill that analyzes ASP.NET Core MVC projects across architecture, security, database, performance, testing, and code quality.

It does not merely scan your code. It tries to understand your architecture, collect evidence, and create a safe refactoring path.

---

## 🚀 What is SEZER AI MVC?

SEZER AI MVC is a comprehensive audit, architecture analysis, and refactoring planning skill designed for ASP.NET Core MVC projects.

Its goal is not simply to find "code smells".

The skill:

- discovers the repository structure,
- identifies the existing architecture,
- analyzes controller and service responsibilities,
- checks MVC contracts,
- examines the Entity Framework Core and migration chain,
- evaluates security and performance risks,
- analyzes test coverage,
- identifies dead / duplicate / incomplete code candidates,
- investigates cross-layer dependencies,
- can perform semantic dependency analysis with CodeGraph,
- creates an evidence-backed refactoring plan.

And by default, all of this is performed in:

> READ_ONLY

mode.

---

## ✨ Core Features

### 🏗️ Architecture Audit

It tries to understand which architecture is actually being used in the project.

Example evaluations:

- Traditional Layered Architecture
- MVC Monolith
- Vertical Slice Architecture
- Clean Architecture
- Modular Monolith
- Hybrid architectures

The skill does not recommend an architecture simply because it is popular.

Priority:

> The simplest solution that is appropriate and sufficient for the project.

---

### 🎯 ASP.NET Core MVC Analysis

It analyzes the MVC layer in detail:

- Controllers
- Actions
- Views
- ViewModels
- Partial Views
- Layouts
- ViewComponents
- Routing
- Model Validation
- Authorization
- Form → Action contracts

The goal is not merely to count files, but to understand the actual relationships between layers.

---

### 🧩 Controller Responsibility Analysis

It analyzes responsibilities found in controllers, such as:

- business logic
- persistence logic
- transaction orchestration
- validation logic
- external service calls
- direct DbContext usage

However, it does not automatically try to move every controller responsibility into a service layer.

Responsibilities belonging to HTTP and MVC remain in the controller.

---

## 🗄️ EF Core & Database Truth Analysis

SEZER AI MVC separates different levels of truth during database analysis:

```text
Entity Model
    ↓
EF Configuration
    ↓
DbContext Model
    ↓
Migrations
    ↓
Expected Schema
    ↓
Live Database
```

If live database access is unavailable, it does not claim:

> Live DB verified

This distinction is one of the skill's core principles for reducing incorrect database conclusions.

---

## 🔐 Security Audit

Security analysis follows an evidence-first approach.

Example areas checked:

- Authentication
- Authorization
- Cookie configuration
- Anti-forgery
- File upload validation
- Secret/configuration usage
- Exception handling
- Security headers
- Rate limiting
- Sensitive logging
- Hard-coded configuration
- Input validation

A risk is not automatically classified as HIGH or CRITICAL based only on its category.

Severity evaluation considers:

- evidence strength
- exposure
- exploitability
- preconditions
- technical impact
- business impact
- compensating controls

---

## ⚡ Performance Audit

The skill analyzes potential performance issues such as:

- N+1 query patterns
- unnecessary database round-trips
- repeated queries
- synchronous I/O
- large controller operations
- caching opportunities
- response optimization
- query projection problems

However, when no benchmark has been performed, it does not present unmeasured performance assumptions as facts.

---

## 🧪 Testing Audit

The project is evaluated for:

- Unit Tests
- Integration Tests
- Architecture Tests
- Test projects
- Refactoring safety nets

If tests are absent, the skill does not hide that fact.

For example:

```text
Test Discovery: COMPLETED
Test Execution: NOT_EXECUTED
Testing Assessment: FINDINGS_PRESENT
```

can be produced as separate results.

---

## 🕸️ CodeGraph Semantic Analysis

When CodeGraph integration is available, SEZER AI MVC can use semantic code analysis.

Example use cases:

- caller / callee analysis
- dependency direction
- symbol relationships
- blast radius analysis
- circular dependency investigation
- refactoring impact analysis

However:

```text
.codegraph directory exists
```

alone is not proof of execution.

The skill requires actual evidence that CodeGraph was executed.

---

## 🔍 Cross-Layer Analysis

The skill does not inspect files only in isolation.

When possible, it follows the chain:

```text
View
 ↓
ViewModel
 ↓
Controller
 ↓
Application / Service
 ↓
Domain
 ↓
Entity
 ↓
EF Configuration
 ↓
DbContext
 ↓
Migration
 ↓
Database
```

The goal is not merely to determine whether individual layers look correct, but whether they work correctly together.

---

## 🧹 Code Quality Analysis

The Full Audit also evaluates:

- Dead code
- Duplicate code
- Incomplete implementations
- TODO / FIXME
- NotImplementedException
- Empty catch blocks
- Placeholder flows
- Repeated business rules
- Suspicious unused symbols

Because of reflection, Dependency Injection, and framework conventions, a static-analysis result does not directly lead to a "delete" decision.

---

## 🧭 Feature Gap Analysis

The skill can investigate missing or incomplete features based on behavior observed in the repository.

Example classifications:

```text
CONFIRMED_DEFECT
CONFIRMED_INCOMPLETE_IMPLEMENTATION
PROBABLE_FEATURE_GAP
ARCHITECTURAL_OPPORTUNITY
PRODUCT_SUGGESTION
INSUFFICIENT_EVIDENCE
```

The skill does not invent new product features.

---

## 🧠 Evidence-Driven Analysis

The core principle of SEZER AI MVC is:

> No certainty without evidence.

Whenever possible, every important finding follows this chain:

```text
Source Evidence
      ↓
Interpretation
      ↓
Cross-check
      ↓
Finding
      ↓
Confidence
      ↓
Recommendation
```

If the build was not executed:

```text
Build: NOT_EXECUTED
```

If the live database was not accessed:

```text
Live DB: NOT_EXECUTED
```

If CodeGraph was not executed:

```text
CodeGraph: NOT_EXECUTED
```

---

## 🧮 Canonical Capability Validation

In the next-generation Full Audit flow, capability states are managed through a single canonical matrix.

```text
Canonical Capability Matrix
          ↓
Physical Row Validation
          ↓
Unique Capability IDs
          ↓
Applicability / Execution Aggregation
          ↓
Arithmetic Validation
          ↓
Invariant Checks
          ↓
Overall Audit Status
```

The goal is for the AI to be able to validate even the numbers in its own report.

When possible, the following artifact is generated:

```text
.sezer-audit/capability-validation.json
```

---

## 🛡️ READ_ONLY By Default

One of the important security rules of SEZER AI MVC is:

> Performing an audit does not mean changing the code.

Default behavior:

```text
READ_ONLY
```

Without explicit user permission, the skill does not:

- modify source code
- generate migrations
- modify the database
- modify configuration
- apply refactoring

It analyzes first.

Then it creates a plan.

Changes require separate permission.

---

## 📊 Full Audit Outputs

A typical Full Audit may create reports under `.sezer-audit`:

```text
.sezer-audit/
│
├── 00-executive-summary.md
├── repository-inventory.md
├── architecture-audit.md
├── mvc-audit.md
├── application-domain-audit.md
├── database-audit.md
├── security-audit.md
├── performance-audit.md
├── testing-audit.md
├── cross-layer-audit.md
├── findings-register.md
├── refactoring-plan.md
│
├── skil-rapor.md
└── capability-validation.json
```

File names may vary slightly depending on the agent or audit version used.

---

## 🧪 Skill Self-Evaluation

SEZER AI MVC does not only evaluate the repository.

It also attempts to evaluate its own audit performance.

At the end of a Full Audit, it can generate:

```text
skil-rapor.md
```

This report is designed to show:

- which analyses were actually executed,
- where evidence was missing,
- CodeGraph execution status,
- database truth levels,
- capability coverage,
- possible false positives / negatives,
- consistency issues,
- skill rules that need improvement.

This mechanism enables SEZER AI MVC to be iteratively improved on real projects.

---

## 🏛️ Architectural Philosophy

The goal of SEZER AI MVC is not to transform every project into the same architecture.

For example, in a small MVC application:

```text
Controller
   ↓
Application Service
   ↓
DbContext
```

may be sufficient.

It is not always correct to automatically add:

- Repository Pattern
- Clean Architecture
- CQRS
- MediatR
- Modular Monolith
- Microservices

to every project.

The skill first tries to understand the problem.

Then it recommends a solution with the least unnecessary complexity.

---

## 🧰 Example Usage

You can give an AI agent a task such as:

```text
Perform a FULL AUDIT on this repository using the sezer-ai-mvc skill.

Work mode: READ_ONLY.

The skill's own Full Audit protocol is authoritative.
Create the required audit reports and skil-rapor.md.

Do not apply refactoring.
```

---

## 🤖 Agent-Agnostic Design

SEZER AI MVC is not designed to depend on a specific AI coding agent.

With appropriate integration, the skill can be used with different coding agents.

Comparing the behavior of different agents during development and real-repository testing is also part of the skill's validation process.

---

## 🎯 Project Goal

The goal of SEZER AI MVC is:

> To establish an AI-assisted, evidence-controlled software engineering audit standard for ASP.NET Core MVC repositories.

Rather than being just a code-analysis prompt, it aims to standardize the following workflow:

```text
Discover
   ↓
Understand
   ↓
Verify
   ↓
Audit
   ↓
Cross-check
   ↓
Plan
   ↓
Refactor with permission
   ↓
Verify again
```

---

## 🚧 Development Status

### 🧪 Active Development

SEZER AI MVC is being iteratively tested on real ASP.NET Core MVC projects.

Each test cycle follows:

```text
audit → evidence review → skill self-evaluation → rule hardening
```

---

## 🤝 Contributing

Bug reports, false-positive examples, architecture edge cases, and real repository test results are especially valuable.

When contributing, it is helpful to provide, whenever possible:

- repository context
- finding evidence
- expected behavior
- actual behavior
- agent/tool information used

---

## 👨‍💻 SEZER AI

AI • Software Engineering • Architecture • Automation

sezerdeveloper@gmail.com

### ⭐ Evidence First. Architecture Second. Refactor With Permission.
