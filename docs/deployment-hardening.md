# Deployment Hardening

Bu dosya, frontend ağırlıklı projeleri Vercel, Netlify, Cloudflare Pages veya benzeri platformlarda yayına almadan önce yapılabilecek temel güvenlik ve kalite kontrollerini açıklar.

Bu tam kapsamlı bir cloud security rehberi değildir. Amaç; statik veya frontend ağırlıklı projelerde en sık unutulan yayın ayarlarını görünür hale getirmektir.

## 1. Production ve preview ortamını ayır

Preview deployment, her branch veya pull request için yararlıdır; ancak production ile aynı kabul edilmemelidir.

Kontrol:

- Preview ortamı production kullanıcılarına açık mı?
- Preview linkleri hassas veya bitmemiş özellik gösteriyor mu?
- Preview ortamında test/debug metinleri var mı?
- Production API veya secret değerleri preview’da gereksiz yere kullanılıyor mu?

Kural: Preview ortamı test kolaylığı sağlar; güvenlik sınırlarının dışında düşünülmemelidir.

## 2. Environment variable kontrolü

Frontend projelerinde `VITE_`, `NEXT_PUBLIC_` gibi prefix’lerle başlayan değişkenler client bundle içine girebilir.

Kontrol:

- Public değişkenlerin gerçekten public olması uygun mu?
- Secret, token, private key, admin endpoint veya internal URL client tarafına çıkıyor mu?
- `.env`, `.env.local`, `.env.production` dosyaları Git’e eklenmiş mi?

Kural: Client tarafına çıkan hiçbir değer secret kabul edilmemelidir.

## 3. Secret’ları repoya koyma

AI agent’lar bazen örnek config üretirken gerçek değer formatına benzeyen dummy secret’lar yazabilir.

Kontrol:

- `.env` dosyaları `.gitignore` içinde mi?
- Repo içinde API key, token, webhook secret, private key veya servis credential var mı?
- README veya örnek dokümanlarda gerçek değer paylaşılmış mı?

Öneri: Sadece `.env.example` paylaş; gerçek değerleri deployment platformunun secret/env yönetiminde tut.

## 4. Custom domain + HTTPS kontrolü

Yayına çıkmadan önce domain ve TLS davranışı test edilmelidir.

Kontrol:

- Custom domain doğru production deployment’a mı bağlı?
- HTTPS aktif mi?
- HTTP istekleri HTTPS’e yönleniyor mu?
- Alt domainler aynı güvenlik beklentisine sahip mi?
- HSTS ayarı domain yapısına uygun mu?

HSTS `includeSubDomains` ve `preload`, domain yapısı tam stabil olmadan eklenmemelidir.

## 5. Security headers uygula

Header’lar platforma göre farklı şekilde tanımlanabilir.

- Vercel: `vercel.json`
- Netlify: `_headers` veya `netlify.toml`
- Cloudflare: Transform Rules / Rulesets
- Custom server: reverse proxy veya app server konfigürasyonu

Başlangıç için `docs/security-headers.md` dosyasındaki baseline incelenebilir.

## 6. Üçüncü parti scriptleri sınırlandır

Yayın öncesi tüm script kaynaklarını listele.

Kontrol:

- Analytics gerekli mi?
- Chat widget gerekli mi?
- Embed gerekli mi?
- Script hangi domain’den geliyor?
- Kullanıcı davranışı veya kişisel veri toplanıyor mu?
- Privacy metni bu akışı açıklıyor mu?

Kural: “Belki lazım olur” diye üçüncü parti script eklenmemelidir.

## 7. Analytics/tracking kararını bilinçli ver

Analytics kullanmak kötü değildir; ancak veri akışı açıklanmalıdır.

Kontrol:

- Hangi olaylar izleniyor?
- IP, user agent, referrer veya device bilgisi işleniyor mu?
- Kullanıcıya açıklandı mı?
- Çerez veya local storage kullanılıyor mu?
- Consent gereksinimi var mı?

Kural: Privacy iddiası, gerçek analytics/tracking davranışıyla çelişmemelidir.

## 8. Build output kontrolü

AI ile geliştirmede gereksiz dosyalar build çıktısına veya public klasöre karışabilir.

Kontrol:

- Test dosyaları public’e çıktı mı?
- Eski mock data veya debug JSON dosyaları yayınlandı mı?
- Kaynak haritaları production’da gerekli mi?
- Büyük medya dosyaları optimize edildi mi?
- Kullanılmayan route veya demo sayfaları kaldı mı?

## 9. Form ve veri toplama kontrolü

Form varsa frontend artık yalnızca görsel arayüz değildir; veri akışı başlar.

Kontrol:

- Hangi veri toplanıyor?
- Veri nereye gidiyor?
- Hata durumunda veri loglanıyor mu?
- Kullanıcıya açıkça söyleniyor mu?
- Gereksiz alan var mı?
- Bot/spam koruması var mı?

Kural: Veri toplama, tasarım kararı değil güvenlik ve gizlilik kararıdır.

## 10. Yayın sonrası manuel kontrol

Deployment bittikten sonra yalnızca “site açılıyor mu?” diye bakmak yeterli değildir.

Kontrol:

- Header’lar canlı ortamda görünüyor mu?
- Console error var mı?
- CSP violation var mı?
- Lighthouse/Web Vitals sonuçları kabul edilebilir mi?
- Mobil görünüm bozuluyor mu?
- Klavye ile navigasyon yapılabiliyor mu?
- Formlar beklenen şekilde çalışıyor mu?
- 404 ve hata sayfaları düzgün mü?

## 11. AI agent deployment stop koşulları

AI aşağıdaki durumlarda deployment değişikliğini otomatik yapmamalı; önce kullanıcıya risk açıklamalıdır:

- Yeni secret/env variable ekleniyorsa
- Security header gevşetiliyorsa
- CSP içine yeni domain ekleniyorsa
- Analytics/tracking script’i ekleniyorsa
- Form veya veri toplama davranışı değişiyorsa
- Production domain/redirect ayarı değişiyorsa
- Public klasöre yeni dosya ekleniyorsa

## Kısa özet

Deployment hardening, projeyi karmaşıklaştırmak için değil; yayına çıkmadan önce basit ama kritik hataları azaltmak için yapılır.

İyi bir frontend deployment:

- HTTPS kullanır.
- Secret sızdırmaz.
- Preview ve production ayrımını bilir.
- Üçüncü parti scriptleri gerekçelendirir.
- Security headers’ı test ederek uygular.
- Privacy iddialarını gerçek veri akışıyla uyumlu tutar.
