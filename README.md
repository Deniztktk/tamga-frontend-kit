# Tamga Frontend Kit

AI destekli frontend geliştirme süreçlerinde daha tutarlı, erişilebilir, güvenli ve “AI template” gibi görünmeyen arayüzler üretmek için hazırlanmış açık kaynak workflow kit’i.

> Vibe coding’i yasaklamıyoruz; kontrolsüz vibe coding’i profesyonel workflow’a çeviriyoruz.

Bu repo, Tamga 30 içerik serisinin 1. günü için hazırlanmış pratik bir başlangıç kit’idir. Tamga 30’un tamamı AI rehberi değildir; bu repo yalnızca bugünkü “AI ile jenerik olmayan frontend workflow” konusuna eşlik eder. Amaç yalnızca araç listelemek değil; AI ile üretim yaparken tasarım sistemi, component disiplini, prompt/rules yaklaşımı, erişilebilirlik, performans, dependency kontrolü, security headers ve deployment hardening konularını birlikte düşünmektir.

## Bu repo neyi çözer?

AI araçlarıyla web arayüzü üretmek hız kazandırır; ancak belirsiz promptlar ve kontrolsüz agent akışları genellikle şu sorunlara yol açar:

- Aynı görünen hero bölümleri, kartlar, gradientler ve “modern SaaS” klişeleri
- Rastgele Tailwind class yığınları ve tutarsız component kullanımı
- Gereksiz dependency eklenmesi
- Font, ikon, spacing ve motion sisteminin dağılması
- Accessibility kontrollerinin unutulması
- Üçüncü parti script, analytics, CDN ve font kaynaklarının sorgulanmadan eklenmesi
- “Güvenli”, “privacy-first”, “local-only” gibi iddiaların gerçek mimariyle uyuşmaması

Tamga Frontend Kit bu sorunları tek bir “mucize araç” ile değil, uygulanabilir kurallar, checklist’ler ve güvenli yayın kontrolleriyle ele alır.

## Kime yönelik?

Bu repo özellikle şunlar için hazırlanmıştır:

- AI destekli web sitesi geliştiren frontend geliştiriciler
- Cursor, Claude Code, Codex, v0, Lovable, Bolt gibi araçlarla çalışan üreticiler
- Kişisel site, portfolyo, landing page veya küçük ürün arayüzü geliştirenler
- Tasarım sistemi ve frontend güvenliğini birlikte düşünmek isteyenler
- Açık kaynak projelerde daha kontrollü frontend workflow kurmak isteyenler

## Ne değildir?

Bu repo:

- Eksiksiz bir frontend kursu değildir.
- Her proje için tek doğru stack önerisi değildir.
- Tam kapsamlı cloud security rehberi değildir.
- Backend, auth, ödeme veya veri tabanı mimarisi rehberi değildir.
- “%100 güvenli site” vaadi vermez.
- Exploit, bypass, jailbreak, saldırı rehberi veya kötüye kullanım yönlendirmesi içermez.

## İlk release içinde neler var?

```txt
README.md
LICENSE
docs/
  recommended-stack.md
  security-headers.md
  deployment-hardening.md
rules/
  design.md
  cursorrules-template.md
  claude-md-template.md
  ai-stop-rules.md
checklists/
  pre-deploy-checklist.md
prompts/
  premium-hero-prompt.md
examples/
  vercel-security-headers.json
```

## Önerilen kullanım akışı

1. `docs/recommended-stack.md` dosyasını okuyarak proje için hangi katmanlara ihtiyacın olduğunu belirle.
2. `rules/design.md` dosyasını kendi marka, ürün ve tasarım diline göre düzenle.
3. Cursor kullanıyorsan `rules/cursorrules-template.md`, Claude Code kullanıyorsan `rules/claude-md-template.md` dosyasını proje köküne uyarlayarak ekle.
4. AI’a üretim yaptırmadan önce `rules/ai-stop-rules.md` içindeki stop koşullarını workflow’a dahil et.
5. UI üretimi için `prompts/premium-hero-prompt.md` dosyasındaki prompt mantığını kendi projene göre özelleştir.
6. Yayına çıkmadan önce `checklists/pre-deploy-checklist.md`, `docs/security-headers.md` ve `docs/deployment-hardening.md` dosyalarıyla son kontrol yap.


## Vercel security headers örneği hakkında

`examples/vercel-security-headers.json` dosyası doğrudan her projeye körlemesine kopyalanacak bir garanti yapılandırması değildir. Vercel’de kullanılacaksa proje kökünde `vercel.json` olarak uyarlanmalı; harici font, analytics, iframe, API, chat widget, ödeme sağlayıcısı veya embed kullanılıyorsa CSP bilinçli şekilde güncellenmelidir.

## Güvenli kapsam notu

Tamga Frontend Kit, frontend üretim sürecinde güvenlik farkındalığını artırmayı hedefler. Buradaki öneriler savunma ve kalite kontrol amaçlıdır. Security headers, dependency kontrolü veya deployment hardening gibi başlıklar tek başına güvenlik garantisi sağlamaz; ancak iyi bir başlangıç denetimi sunar.

Projelerde kullanıcı verisi, form, analytics, auth, ödeme, üçüncü parti script veya backend entegrasyonu varsa; teknik, hukuki ve gizlilik etkileri ayrıca değerlendirilmelidir.

## Katkı çağrısı

Katkılar şu alanlarda özellikle değerlidir:

- Daha iyi rules/template örnekleri
- Accessibility checklist geliştirmeleri
- Security header örneklerinin platformlara göre iyileştirilmesi
- AI ile üretilmiş jenerik UI pattern’lerini tespit eden örnekler
- Savunma odaklı frontend kalite kontrol notları

Katkı gönderirken lütfen savunma odaklı kapsamı koruyun. Exploit, bypass, saldırı rehberi, jailbreak veya kötüye kullanım yönlendirmesi içeren katkılar kabul edilmez.

## Kısa kapanış

AI hız sağlar; profesyonel sonuç ise tasarım sistemi, erişilebilirlik, güvenlik ve insan kararıyla oluşur.
