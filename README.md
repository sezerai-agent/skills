# 🧠 SEZER AI MVC

### Evidence-Driven ASP.NET Core MVC Audit & Refactoring Skill
<img src="tr-skills.png" alt="SEZER AI Banner" width="100%">

An AI-powered software engineering skill for auditing and refactoring
ASP.NET Core MVC applications with an evidence-first approach.

**Architecture · Security · EF Core · Database · Performance · Testing · Code Analysis**

> Evidence First. Architecture Second. Refactor With Permission.

<div align="center">

![Profile Views](https://komarev.com/ghpvc/?username=sezerai&color=blue&style=for-the-badge)
![GitHub Followers](https://img.shields.io/github/followers/sezerai?style=for-the-badge&logo=github)
![GitHub Stars](https://img.shields.io/github/stars/sezerai?affiliations=OWNER%2CCOLLABORATOR&style=for-the-badge&logo=github)

### 🤖 Yapay Zeka & Yazılım Mühendisi | AI & Software Engineer

**"Gelecek, zekayı mühendisliğe dönüştürenlerindir."**

[![Portfolio](https://img.shields.io/badge/🌐_Portfolio-Website-0078D4?style=for-the-badge&logo=google-chrome&logoColor=white)](https://kobisme.com.tr)
[![LinkedIn](https://img.shields.io/badge/💼_LinkedIn-Profile-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](#)
[![Email](https://img.shields.io/badge/📧_Email-Contact-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:sezerdeveloper@gmail.com)

</div>

---

## 📊 GitHub Analytics

<div align="center">



![GitHub Streak](https://streak-stats.demolab.com/?user=sezerai&theme=radical&hide_border=true)



</div>

---

# 🧠 SEZER AI MVC

### Evidence-Driven ASP.NET Core MVC Audit & Refactoring Skill

**ASP.NET Core MVC projelerini mimari, güvenlik, veri tabanı, performans, test ve kod kalitesi açısından analiz eden gelişmiş AI skill.**

![ASP.NET Core](https://img.shields.io/badge/ASP.NET_Core-MVC-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)
![Architecture](https://img.shields.io/badge/Architecture-Audit-1F6FEB?style=for-the-badge)
![CodeGraph](https://img.shields.io/badge/CodeGraph-Semantic_Analysis-8A2BE2?style=for-the-badge)
![Mode](https://img.shields.io/badge/Default-READ_ONLY-success?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active_Development-orange?style=for-the-badge)

**Kodunu sadece taramaz.  
Mimarini anlamaya, kanıt toplamaya ve güvenli bir refactoring yolu çıkarmaya çalışır.**

</div>

---

## 🚀 SEZER AI MVC Nedir?

**SEZER AI MVC**, ASP.NET Core MVC projeleri için geliştirilmiş kapsamlı bir **audit, architecture analysis ve refactoring planning skill**'idir.

Amaç yalnızca "kod kokusu" bulmak değildir.

Skill;

- repository yapısını keşfeder,
- mevcut mimariyi tespit eder,
- controller ve service sorumluluklarını analiz eder,
- MVC contract'larını kontrol eder,
- Entity Framework Core ve migration zincirini inceler,
- güvenlik ve performans risklerini değerlendirir,
- test kapsamını analiz eder,
- dead / duplicate / incomplete code adaylarını tespit eder,
- cross-layer bağımlılıkları inceler,
- CodeGraph ile semantic dependency analizi yapabilir,
- evidence-backed refactoring planı oluşturur.

Ve bütün bunları varsayılan olarak:

> **READ_ONLY**

modunda gerçekleştirir.

---

## ✨ Temel Özellikler

### 🏗️ Architecture Audit

Projede gerçekte hangi mimarinin kullanıldığını anlamaya çalışır.

Örnek değerlendirmeler:

- Traditional Layered Architecture
- MVC Monolith
- Vertical Slice Architecture
- Clean Architecture
- Modular Monolith
- Hybrid yapılar

Skill popüler olduğu için bir mimariyi önermez.

Öncelik:

> **Projeye en uygun ve en basit yeterli çözüm.**

---

### 🎯 ASP.NET Core MVC Analizi

MVC katmanını detaylı olarak inceler:

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
- Form → Action contract'ları

Amaç yalnızca dosya saymak değil, katmanlar arasındaki gerçek ilişkiyi anlamaktır.

---

### 🧩 Controller Responsibility Analysis

Controller'larda bulunan:

- business logic
- persistence logic
- transaction orchestration
- validation logic
- external service calls
- direct DbContext usage

gibi sorumlulukları analiz eder.

Ama her controller'ı otomatik olarak service layer'a taşımaya çalışmaz.

HTTP ve MVC'ye ait sorumluluklar controller'da kalır.

---

## 🗄️ EF Core & Database Truth Analysis

SEZER AI MVC database analizinde farklı doğruluk seviyelerini birbirinden ayırır:

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
````

Live database erişimi yoksa:

> **Live DB verified**

iddiasında bulunmaz.

Bu ayrım, yanlış database sonuçlarını azaltmak için skill'in temel prensiplerinden biridir.

---

## 🔐 Security Audit

Security analizi evidence-first yaklaşımıyla yapılır.

Kontrol edilen örnek alanlar:

* Authentication
* Authorization
* Cookie configuration
* Anti-forgery
* File upload validation
* Secret/configuration usage
* Exception handling
* Security headers
* Rate limiting
* Sensitive logging
* Hard-coded configuration
* Input validation

Bir risk yalnızca kategorisine bakılarak **HIGH** veya **CRITICAL** yapılmaz.

Severity değerlendirmesinde:

* evidence strength
* exposure
* exploitability
* preconditions
* technical impact
* business impact
* compensating controls

dikkate alınır.

---

## ⚡ Performance Audit

Skill potansiyel performans sorunlarını analiz eder:

* N+1 query patterns
* gereksiz database round-trip'leri
* repeated queries
* synchronous I/O
* büyük controller işlemleri
* caching fırsatları
* response optimization
* query projection problemleri

Ancak benchmark yapılmadıysa ölçülmemiş performans sonuçlarını gerçekmiş gibi göstermez.

---

## 🧪 Testing Audit

Projede:

* Unit Tests
* Integration Tests
* Architecture Tests
* Test projects
* Refactoring safety net

incelenir.

Test yoksa bunu gizlemez.

Örneğin:

```text
Test Discovery: COMPLETED
Test Execution: NOT_EXECUTED
Testing Assessment: FINDINGS_PRESENT
```

gibi ayrıştırılmış sonuçlar üretilebilir.

---

## 🕸️ CodeGraph Semantic Analysis

SEZER AI MVC, CodeGraph entegrasyonu mevcut olduğunda semantic code analysis kullanabilir.

Örnek kullanım alanları:

* caller / callee analysis
* dependency direction
* symbol relationships
* blast radius analysis
* circular dependency investigation
* refactoring impact analysis

Ancak:

```text
.codegraph directory exists
```

tek başına execution proof değildir.

Skill gerçek CodeGraph çalıştırma kanıtı ister.

---

## 🔍 Cross-Layer Analysis

Skill yalnızca dosyaları ayrı ayrı incelemez.

Mümkün olduğunda aşağıdaki zinciri takip eder:

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

Amaç katmanların tek tek doğru görünmesinden ziyade, **birlikte doğru çalışıp çalışmadığını** anlamaktır.

---

## 🧹 Code Quality Analysis

Full Audit kapsamında aşağıdaki alanlar da değerlendirilir:

* Dead code
* Duplicate code
* Incomplete implementations
* TODO / FIXME
* NotImplementedException
* Empty catch blocks
* Placeholder flows
* Repeated business rules
* Suspicious unused symbols

Reflection, Dependency Injection ve framework conventions nedeniyle statik analiz sonucu doğrudan "sil" kararı verilmez.

---

## 🧭 Feature Gap Analysis

Skill repository'de görülen davranışlardan hareketle eksik veya yarım kalmış feature'ları araştırabilir.

Örnek sınıflandırmalar:

```text
CONFIRMED_DEFECT
CONFIRMED_INCOMPLETE_IMPLEMENTATION
PROBABLE_FEATURE_GAP
ARCHITECTURAL_OPPORTUNITY
PRODUCT_SUGGESTION
INSUFFICIENT_EVIDENCE
```

Skill yeni ürün özellikleri uydurmaz.

---

## 🧠 Evidence-Driven Analysis

SEZER AI MVC'nin temel prensibi:

> **Evidence yoksa kesinlik yok.**

Her önemli finding mümkün olduğunda şu zinciri izler:

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

Build çalıştırılmadıysa:

```text
Build: NOT_EXECUTED
```

Live DB okunmadıysa:

```text
Live DB: NOT_EXECUTED
```

CodeGraph çalışmadıysa:

```text
CodeGraph: NOT_EXECUTED
```

---

## 🧮 Canonical Capability Validation

Yeni nesil Full Audit akışında capability durumları tek bir canonical matrix üzerinden yönetilir.

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

Amaç AI'ın kendi raporundaki sayıları bile doğrulayabilmesidir.

Mümkün olduğunda:

```text
.sezer-audit/capability-validation.json
```

artifact'ı oluşturulur.

---

## 🛡️ READ_ONLY By Default

SEZER AI MVC'nin önemli güvenlik kurallarından biri:

> **Audit yapmak, kodu değiştirmek anlamına gelmez.**

Varsayılan davranış:

```text
READ_ONLY
```

Skill kullanıcı açıkça izin vermeden:

* source code değiştirmez
* migration üretmez
* database değiştirmez
* configuration değiştirmez
* refactoring uygulamaz

Önce analiz eder.

Sonra plan çıkarır.

Değişiklik için ayrıca izin ister.

---

## 📊 Full Audit Çıktıları

Tipik bir Full Audit sonunda `.sezer-audit` altında raporlar oluşturulabilir:

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

Dosya isimleri kullanılan agent veya audit sürümüne göre küçük farklılıklar gösterebilir.

---

## 🧪 Skill Self-Evaluation

SEZER AI MVC yalnızca repository'yi değerlendirmez.

Kendi audit performansını da değerlendirmeye çalışır.

Full Audit sonunda:

```text
skil-rapor.md
```

üretilebilir.

Bu rapor skill'in:

* hangi analizleri gerçekten çalıştırdığını,
* hangi alanlarda evidence eksik olduğunu,
* CodeGraph execution durumunu,
* database truth seviyelerini,
* capability coverage durumunu,
* possible false positives / negatives,
* consistency problemlerini,
* geliştirilmesi gereken skill kurallarını

göstermek için tasarlanmıştır.

Bu mekanizma SEZER AI MVC'nin gerçek projeler üzerinde iteratif olarak geliştirilebilmesini sağlar.

---

## 🏛️ Mimari Felsefe

SEZER AI MVC'nin amacı her projeyi aynı mimariye çevirmek değildir.

Örneğin küçük bir MVC uygulamasında:

```text
Controller
   ↓
Application Service
   ↓
DbContext
```

yeterli olabilir.

Her projeye otomatik olarak:

* Repository Pattern
* Clean Architecture
* CQRS
* MediatR
* Modular Monolith
* Microservices

eklemek doğru değildir.

Skill önce problemi anlamaya çalışır.

Sonra en düşük gereksiz karmaşıklıkla çözüm önerir.

---

## 🧰 Örnek Kullanım

AI agent'a:

```text
Bu repository üzerinde sezer-ai-mvc skill'ini kullanarak FULL AUDIT gerçekleştir.

Çalışma modu READ_ONLY.

Skill'in kendi Full Audit protokolü authoritative'dir.
Gerekli audit raporlarını ve skil-rapor.md dosyasını oluştur.

Refactoring uygulama.
```

şeklinde görev verilebilir.

---

## 🤖 Agent-Agnostic Design

SEZER AI MVC belirli bir AI coding agent'a bağlı olacak şekilde tasarlanmamıştır.

Skill uygun entegrasyon sağlandığında farklı coding agent'larla kullanılabilir.

Geliştirme ve gerçek repository testlerinde farklı agent davranışlarının karşılaştırılması da skill'in doğrulama sürecinin bir parçasıdır.

---

## 🎯 Projenin Hedefi

SEZER AI MVC'nin hedefi:

> **ASP.NET Core MVC repository'lerinde AI destekli fakat evidence kontrollü bir yazılım mühendisliği audit standardı oluşturmak.**

Kod analizi yapan bir prompt olmaktan ziyade:

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

akışını standartlaştırmayı hedefler.

---

## 🚧 Development Status

<div align="center">

### 🧪 Active Development

SEZER AI MVC gerçek ASP.NET Core MVC projeleri üzerinde iteratif olarak test edilmektedir.

Her test turunda:

**audit → evidence review → skill self-evaluation → rule hardening**

döngüsü uygulanmaktadır.

</div>

---

## 🤝 Katkı

Bug report, false-positive örnekleri, architecture edge-case'leri ve gerçek repository test sonuçları özellikle değerlidir.

Katkı yaparken mümkün olduğunca:

* repository context
* finding evidence
* expected behavior
* actual behavior
* kullanılan agent/tool bilgisi

paylaşılması faydalıdır.

---

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


----

## 👨‍💻 SEZER AI

<div align="center">

**AI • Software Engineering • Architecture • Automation**

[![GitHub](https://img.shields.io/badge/GitHub-SEZER_AI-181717?style=for-the-badge\&logo=github)](https://github.com/sezerai)
[![Website](https://img.shields.io/badge/Website-sezerai.tr-0078D4?style=for-the-badge\&logo=googlechrome\&logoColor=white)](https://sezerai.tr)
[![Email](https://img.shields.io/badge/Email-Contact-D14836?style=for-the-badge\&logo=gmail\&logoColor=white)](mailto:sezerdeveloper@gmail.com)

### ⭐ Evidence First. Architecture Second. Refactor With Permission.

</div>
