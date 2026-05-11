# geliştirici günlüğü (devlog)

## 2026-05-11 — Agent discovery sadeleştirmesi

**Amaç:** Checklist için “tam görünür” metadata yerine statik bir bilgi sitesinin **gerçekten sahip olduğu** yeteneklerle uyumlu, az bakım gerektiren bir keşif katmanı bırakmak.

**Kaldırılan / kapsam dışına alınan (sahte veya gereksiz capability):**

- `openapi.yaml`, `service-desc`, sağlık/`status` uçları — gerçek bir HTTP API veya operasyonel health endpoint yoktu.
- `/.well-known/oauth-protected-resource` ve OAuth/OIDC keşif belgeleri — kimlik doğrulamalı API yok; bu dosyalar yine de “korumalı kaynak” iması verebiliyordu.
- `/.well-known/mcp/server-card.json` ve `index.html` içi WebMCP — barındırılan bir MCP sunucusu ve tarayıcı aracı yürütme yoktu.
- `index.html` ve `_headers` içindeki MCP / `describedby` / OpenAPI / status keşif bağlantıları.

**Korunan minimal set:** `.nojekyll`, `homepage.md`, `/.well-known/api-catalog` (yalnızca `service-doc` + Markdown `alternate`), `docs/api.html` (makine-okur kaynakların dürüst özeti), `_headers` (yalnızca üç `Link` + `Vary` + `homepage.md` Content-Type), `/.well-known/agent-skills/*` (yalnızca site özeti, gezinme, içerik keşfi; araç/API iddiası yok).

**Neden minimal:** Edge’de `Link` ve `text/markdown` başlıkları yine `_headers` ile uygulanabilir; içerik ve ilişkiler tek kaynakta tutulunca drift ve yanlış pozitif audit sonuçları azalır.

**Not:** `.gitignore` içindeki `*.md` istisnaları (`README.md`, `homepage.md`, `devlog.md`, `.well-known/**/*.md`) hâlâ gerekli; aksi halde Markdown dosyaları repo dışına düşebilir.

---

## 2026-05-11 — İlk agent-ready denemesi (tarihsel)

İlk turda RFC 9727 linkset’e ek olarak OpenAPI placeholder, durum JSON’u, OAuth korumalı kaynak meta verisi, MCP kartı ve WebMCP araçları eklenmişti. Yukarıdaki sadeleştirme ile bu yaklaşım **geri alındı**; depo yalnızca gerçek statik yayın modeline uygun keşfi tutar.
