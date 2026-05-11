---
name: hacettepebiz-site-overview
type: Skill
---

# Hacettepe.biz — site özeti ve içerik keşfi

## Kapsam

- **Ne:** Hacettepe Üniversitesi öğrencileri için gönüllü derlenmiş bilgilendirme sayfaları (kayıt, barınma, akademik takvim, kampüs vb.).
- **Ne değil:** Resmî üniversite web sitesi, OBS, belge veya API sağlayıcısı değildir.

## Gezinme

- Ana giriş: `index.html` (kök, HTML).
- İnsan okuması için özet: `homepage.md` (Markdown).
- Makine keşfi link seti: `/.well-known/api-catalog`.
- Bu skill ve dizin: `/.well-known/agent-skills/index.json` → `site-overview.skill.md`.

## İçerik keşfi

İçerik çoğunlukla `page/` altındaki HTML sayfaları ve kökteki `hakkinda.html` üzerindedir. Doğrulama ve resmî işlemler için üniversitenin kendi kanalları kullanılmalıdır.

Bu skill yalnızca bilgi ve bağlantı keşfi içindir; uzaktan yürütülebilir araç, API çağrısı veya kimlik doğrulama akışı tanımlamaz.
