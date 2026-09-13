# Changelog - sezer-ai-mvc

## v1.3-test
Deterministic Completion and Consistency Gates (17 yeni kural)

- Full Audit icin 21 maddelik zorunlu yetenek matrisi (hicbir asama sessizce atlanamaz)
- INV-001 - INV-013: otomatik tutarlilik kurallari (orn. "Live DB denetlenmediyse dogrulandi denemez")
- Repository Pattern artik sadece somut gerekceyle onerilebilir (varsayilan oneri degil)
- Guvenlik bulgulari icin kanit siniflandirmasi (CONFIRMED / STRONGLY_INDICATED / POTENTIAL / UNKNOWN_REQUIRES_VERIFICATION) - erisim eksikligi artik zafiyet kaniti sayilmiyor
- Bos catch bloklari ve hard-coded path'ler otomatik "guvenlik" degil, etkiye gore siniflandiriliyor
- skil-rapor.md artik skill'in kendi zayifliklarini da elestirmek zorunda

## v1.2-test
Evidence Hardening Rules (15 yeni kural)

- CodeGraph Proof-of-Execution: .codegraph klasorunun var olmasi, calistiginin kaniti sayilmaz - gercek komut/sorgu/sonuc kaniti zorunlu
- Execution (COMPLETED/FAILED/...) ile Assessment (FINDINGS_PRESENT/...) ayrimi - "test yok" bulgusu artik "PASSED" olarak yazilamiyor
- Configuration Truth Levels (5 seviye): kod referansi gormek ile degeri gormek ayri kanit seviyeleri
- Coverage, confidence skorunu sinirliyor (orn. 22/32 view incelendiyse %100 iddia edilemez)
- Report Cross-Consistency Check: raporlar arasi celiski kontrolu zorunlu

## v1.1-test
Ilk test surumu - Full Audit, Focused Audit, Refactoring Plan, Architecture Remediation ve Feature Completion Analysis modlarini iceren temel skill.
