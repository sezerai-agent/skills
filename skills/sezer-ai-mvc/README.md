# sezer-ai-mvc

Evidence-driven full audit, CodeGraph-assisted architecture analysis, feature-gap
detection, and controlled refactoring skill for ASP.NET Core MVC solutions.

## Ne Yapar

Bir ASP.NET Core MVC cozumunu bastan sona (solution yapisindan veritabani semasina
kadar) kanita dayali olarak denetler ve refactoring plani uretir:

- Discovery (solution/proje envanteri, teknoloji tespiti)
- Architecture Audit (bagimlilik yonu, moduler sinirlar)
- MVC Audit (Controller -> Action -> ViewModel -> View zinciri)
- Application/Domain Audit
- Database Audit (EF Core, migration, canli sema dogruluk seviyeleri)
- Security / Performance / Testing Audit
- Cross-Layer Audit
- Dependency-aware Refactoring Plan

## Temel Ilkeler

- Varsayilan mod: READ-ONLY. Acik yetkilendirme olmadan hicbir dosya degistirilmez.
- Kanit olmadan bulgu yok. Her bulgu dosya yolu + satir numarasi ile desteklenir.
- Hayali/varsayimsal iddia yasak. CodeGraph gibi araclar gercekten calistirilmadiysa "VERIFIED" denemez.
- Her Full Audit sonunda ayrica skil-rapor.md uretilir - bu, projenin degil, skill'in kendi analiz kalitesinin raporudur.

## Kurulum

SKILL.md dosyasini agent'inin skill klasorune kopyala:

- OpenCode (global): %USERPROFILE%\.config\opencode\skills\sezer-ai-mvc\SKILL.md
- Devin Local / Devin Desktop (global): %APPDATA%\devin\skills\sezer-ai-mvc\SKILL.md

## Kullanim

Full Audit icin: /sezer-ai-mvc yaz, ardindan "Full Audit calistir" de.

Dar kapsamli denetim icin: /sezer-ai-mvc yaz, ardindan "Sadece Architecture Audit (Mode B - Focused Audit) calistir. READ-ONLY kal." de.

## Versiyon Gecmisi

Bkz. CHANGELOG.md

## Lisans

MIT - bkz. repo kokundeki LICENSE dosyasi
