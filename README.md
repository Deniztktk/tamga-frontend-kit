# Tamga Frontend Kit

AI destekli frontend geliştirme süreçlerinde, vibe coding hızını kaybetmeden daha tutarlı, erişilebilir, güvenli ve “AI template” gibi görünmeyen arayüzler üretmek için hazırlanmış açık kaynak workflow kit’i.

> Vibe coding’i yasaklamıyoruz; kontrolsüz vibe coding’i profesyonel workflow’a çeviriyoruz.

Bu repo, **Tamga 30** içerik serisinin **1. günü** için hazırlanmıştır. Tamga 30’un tamamı AI rehberi değildir; bu repo yalnızca bugünün “AI ile jenerik olmayan frontend workflow” konusuna eşlik eder.

---

## Bu repo ne işe yarar?

AI araçlarıyla web sitesi veya arayüz üretirken genelde ilk çıktı hızlı gelir; fakat çoğu zaman şu problemler oluşur:

- Her yerde aynı görünen hero section, kartlar, gradientler ve “modern SaaS” kalıpları
- Tasarım sistemi olmadan yazılmış rastgele Tailwind class’ları
- Birbiriyle uyumsuz font, ikon, spacing, radius ve motion kararları
- Gereksiz dependency eklenmesi
- Accessibility kontrollerinin unutulması
- Üçüncü parti script, analytics, CDN ve font kaynaklarının sorgulanmadan eklenmesi
- “Güvenli”, “privacy-first”, “local-only” gibi iddiaların gerçek mimariyle uyuşmaması

**Tamga Frontend Kit**, bu sorunları tek bir araçla çözmeye çalışmaz. Bunun yerine AI ile üretim yaparken kullanılabilecek:

- tasarım kuralları,
- AI agent sınırları,
- prompt örnekleri,
- yayın öncesi checklist’ler,
- security headers notları,
- deployment hardening kontrolleri

sunar.

Amaç, AI’a sadece “güzel site yap” demek yerine, ona daha net sınırlar ve kalite kriterleri vermektir.

---

## Kime yönelik?

Bu repo özellikle şunlar için hazırlanmıştır:

- Cursor, Claude Code, Codex, v0, Lovable, Bolt gibi araçlarla frontend üretenler
- Kişisel site, portfolyo, landing page veya küçük ürün arayüzü geliştirenler
- AI ile üretilen arayüzlerde “hep aynı tasarım” hissinden çıkmak isteyenler
- Tasarım sistemi, component disiplini ve frontend güvenliğini birlikte düşünmek isteyenler
- Açık kaynak projelerde daha kontrollü frontend workflow kurmak isteyenler

---

## Ne değildir?

Bu repo:

- Eksiksiz bir frontend kursu değildir.
- Her proje için tek doğru stack önerisi değildir.
- Tam kapsamlı cloud security rehberi değildir.
- Backend, auth, ödeme veya veri tabanı mimarisi rehberi değildir.
- “%100 güvenli site” vaadi vermez.
- Exploit, bypass, jailbreak, saldırı rehberi veya kötüye kullanım yönlendirmesi içermez.

---

## Repo içinde ne var?

```txt
tamga-frontend-kit/
├── README.md
├── LICENSE
├── docs/
│   ├── recommended-stack.md
│   ├── security-headers.md
│   └── deployment-hardening.md
├── rules/
│   ├── design.md
│   ├── cursorrules-template.md
│   ├── claude-md-template.md
│   └── ai-stop-rules.md
├── checklists/
│   └── pre-deploy-checklist.md
├── prompts/
│   └── premium-hero-prompt.md
└── examples/
    └── vercel-security-headers.json
```

---

## Dosyalar ne işe yarar?

| Dosya | Ne işe yarar? | Ne zaman kullanılır? |
|---|---|---|
| `docs/recommended-stack.md` | AI destekli frontend için önerilen araç katmanlarını açıklar. | Projeye başlamadan önce hangi araçların ne amaçla kullanılacağını belirlerken. |
| `docs/security-headers.md` | CSP, HSTS, Permissions-Policy, Referrer-Policy gibi temel security header notlarını açıklar. | Yayına çıkmadan önce tarayıcı seviyesindeki savunma kontrollerini düşünürken. |
| `docs/deployment-hardening.md` | Vercel/Netlify/Cloudflare gibi ortamlarda temel yayın güvenliği kontrollerini anlatır. | Preview/production ayrımı, env, secret, domain ve HTTPS kontrolü yaparken. |
| `rules/design.md` | AI’a verilecek tasarım sistemi kurallarını içerir. | AI’a UI üretimi yaptırmadan önce proje tasarım dilini netleştirirken. |
| `rules/cursorrules-template.md` | Cursor için kopyalanabilir proje kuralları sunar. | Cursor ile agentic/frontend geliştirme yaparken. |
| `rules/claude-md-template.md` | Claude Code için `CLAUDE.md` template’i sunar. | Claude Code’un projeyi daha kontrollü okumasını ve değiştirmesini isterken. |
| `rules/ai-stop-rules.md` | AI’ın hangi durumlarda durması, uyarması veya güvenli alternatif önermesi gerektiğini tanımlar. | Dependency, security, privacy, accessibility veya scope değişikliklerinde. |
| `checklists/pre-deploy-checklist.md` | Yayın öncesi kalite, performans, accessibility ve güvenlik kontrol listesi sunar. | Deploy öncesi son kontrol yaparken. |
| `prompts/premium-hero-prompt.md` | Jenerik hero yerine karakterli ve konseptli hero üretmek için örnek prompt verir. | AI’a daha özgün bir ilk ekran tasarlatmak istediğinde. |
| `examples/vercel-security-headers.json` | Vercel için örnek security headers konfigürasyonu sunar. | Vercel projesinde header yapılandırması hazırlarken. |

---

## Önerilen workflow akışları

Bu repo tek bir kullanım şekline sahip değildir. Aşağıdaki üç akış birlikte kullanıldığında daha kontrollü bir frontend üretim süreci oluşur.

### 1. Tasarım hazırlık workflow’u

AI’a kod yazdırmadan önce tasarım yönünü netleştirmek için:

```txt
Referansları seç
↓
Marka / ürün hissini tanımla
↓
rules/design.md dosyasını projeye göre düzenle
↓
Font, renk, spacing, radius ve motion kurallarını netleştir
↓
AI’a üretim yaptırmadan önce bu dosyayı bağlam olarak ver
```

Bu akışın amacı, AI’ın “ortalama güzel” tasarım üretmesini azaltmaktır.

Başlangıç dosyaları:

- `rules/design.md`
- `prompts/premium-hero-prompt.md`
- `docs/recommended-stack.md`

---

### 2. AI agent geliştirme workflow’u

Cursor, Claude Code veya benzeri araçlarla çalışırken:

```txt
Proje amacını tanımla
↓
Cursor kullanıyorsan cursorrules-template.md dosyasını uyarlayıp ekle
↓
Claude Code kullanıyorsan claude-md-template.md dosyasını CLAUDE.md olarak uyarlayıp ekle
↓
AI stop koşullarını projeye dahil et
↓
AI’dan önce plan, sonra değişiklik, sonra doğrulama iste
```

Bu akışın amacı, AI’ın kontrolsüz şekilde dependency eklemesini, tasarım sistemini bozmasını veya güvenlik sınırlarını gevşetmesini engellemektir.

Başlangıç dosyaları:

- `rules/cursorrules-template.md`
- `rules/claude-md-template.md`
- `rules/ai-stop-rules.md`

---

### 3. Yayın öncesi kalite ve güvenlik workflow’u

Site görsel olarak hazır olduğunda yayına çıkmadan önce:

```txt
Build / typecheck / lint kontrolü yap
↓
Responsive ve accessibility kontrolü yap
↓
Dependency ve üçüncü parti scriptleri gözden geçir
↓
Security headers ve CSP davranışını test et
↓
Preview deployment üzerinde manuel kontrol yap
↓
Production deploy sonrası header, Lighthouse ve console kontrolü yap
```

Bu akışın amacı, “site çalışıyor” ile “site yayına hazır” arasındaki farkı kapatmaktır.

Başlangıç dosyaları:

- `checklists/pre-deploy-checklist.md`
- `docs/security-headers.md`
- `docs/deployment-hardening.md`
- `examples/vercel-security-headers.json`

---

## Hızlı başlangıç

### Cursor kullanıyorsan

1. `rules/design.md` dosyasını kendi projenin tasarım diline göre düzenle.
2. `rules/cursorrules-template.md` dosyasını proje köküne `.cursorrules` veya uygun rules dosyası olarak uyarla.
3. `rules/ai-stop-rules.md` içindeki durma koşullarını agent talimatlarına ekle.
4. AI’dan her büyük değişiklik için önce plan, sonra değişiklik, sonra doğrulama iste.

### Claude Code kullanıyorsan

1. `rules/claude-md-template.md` dosyasını proje köküne `CLAUDE.md` olarak uyarla.
2. `rules/design.md` ve `rules/ai-stop-rules.md` dosyalarına referans ver.
3. Claude’dan yeni dependency, security header, veri akışı veya deployment değişikliklerinde önce risk değerlendirmesi istemesini sağla.
4. Her değişiklikten sonra build/test/lint durumunu açıkça raporlamasını iste.

### Sadece rehber olarak kullanıyorsan

1. `docs/recommended-stack.md` dosyasından araç katmanlarını incele.
2. `prompts/premium-hero-prompt.md` dosyasındaki prompt yaklaşımını kendi ürününe göre değiştir.
3. Deploy öncesi `checklists/pre-deploy-checklist.md` dosyasını kontrol listesi olarak kullan.

---

## Önerilen stack yaklaşımı

Bu repo tek bir “zorunlu stack” dayatmaz. Ancak başlangıç için şu katmanları önerir:

```txt
Vite + React + TypeScript
Tailwind CSS
shadcn/ui
Lucide React
Motion / Framer Motion yaklaşımı
Lenis
Fontsource veya self-hosted fontlar
React Router
Biome / ESLint
Vercel
21st.dev
Figma → design.md → Code pipeline
```

Detaylar için: `docs/recommended-stack.md`

Next.js, Astro, Remix veya başka bir framework bazı projelerde daha doğru olabilir. Bu repo’nun amacı framework tartışması yapmak değil; AI destekli üretimde kararların bilinçli verilmesini sağlamaktır.

---

## Security headers örneği hakkında

`examples/vercel-security-headers.json` dosyası Vercel için örnek bir başlangıç konfigürasyonu sunar.

Bu örnek doğrudan her projeye körlemesine kopyalanmamalıdır. Vercel’de kullanılacaksa proje kökünde `vercel.json` olarak uyarlanmalı; harici font, analytics, iframe, API, chat widget, ödeme sağlayıcısı veya embed kullanılıyorsa CSP bilinçli şekilde güncellenmelidir.

Detaylar için:

- `docs/security-headers.md`
- `docs/deployment-hardening.md`

---

## Güvenli kapsam notu

Tamga Frontend Kit, frontend üretim sürecinde güvenlik farkındalığını artırmayı hedefler. Buradaki öneriler savunma ve kalite kontrol amaçlıdır.

Security headers, dependency kontrolü veya deployment hardening gibi başlıklar tek başına güvenlik garantisi sağlamaz; ancak yayın öncesi daha kontrollü bir değerlendirme yapılmasına yardımcı olur.

Projelerde kullanıcı verisi, form, analytics, auth, ödeme, üçüncü parti script veya backend entegrasyonu varsa; teknik, hukuki ve gizlilik etkileri ayrıca değerlendirilmelidir.

---

## Katkı alanları

Katkılar özellikle şu alanlarda değerlidir:

- Daha iyi `design.md` örnekleri
- Cursor / Claude Code / Codex için rules template iyileştirmeleri
- Accessibility checklist geliştirmeleri
- Security header örneklerinin platformlara göre iyileştirilmesi
- AI ile üretilmiş jenerik UI pattern’lerini tespit eden örnekler
- Savunma odaklı frontend kalite kontrol notları
- Gerçek projelerde test edilmiş prompt örnekleri

Katkı gönderirken lütfen savunma odaklı kapsamı koruyun. Exploit, bypass, saldırı rehberi, jailbreak veya kötüye kullanım yönlendirmesi içeren katkılar kabul edilmez.

---

## Kısa özet

AI hız sağlar; profesyonel sonuç ise tasarım sistemi, erişilebilirlik, güvenlik kontrolleri ve insan kararıyla oluşur.

Tamga Frontend Kit’in amacı, AI ile frontend üretirken “hızlı çıktı” ile “yayına hazır ürün” arasındaki boşluğu daha görünür ve yönetilebilir hale getirmektir.
