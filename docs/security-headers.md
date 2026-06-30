# Security Headers

Bu dosya, frontend ağırlıklı projelerde yayın öncesi kontrol edilmesi gereken temel HTTP güvenlik header’larını açıklar.

Security headers tek başına bir siteyi güvenli yapmaz. Ancak tarayıcı seviyesinde bazı riskleri azaltan, iyi bir savunma katmanı oluşturur. Bu rehber statik frontend siteleri, kişisel web siteleri, landing page’ler, portfolyo siteleri ve küçük ürün arayüzleri için başlangıç kontrolü sunar.

## Minimum önerilen header seti

```http
Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: camera=(), microphone=(), geolocation=(), payment=(), usb=()
Content-Security-Policy: default-src 'self'; object-src 'none'; base-uri 'self'; frame-ancestors 'none'; form-action 'self'; img-src 'self' data: https:; font-src 'self' data:; style-src 'self' 'unsafe-inline'; script-src 'self'; connect-src 'self'; upgrade-insecure-requests
```

Bu baseline her projeye doğrudan kopyalanmadan önce test edilmelidir. Analytics, harici font, video embed, ödeme sağlayıcısı, harita, chat widget veya API kullanılıyorsa CSP kaynakları buna göre bilinçli şekilde genişletilmelidir.

## Strict-Transport-Security

```http
Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
```

Tarayıcıya sitenin HTTPS üzerinden kullanılmasını söyler.

Dikkat:

- Domain ve TLS yapılandırması stabil değilse `preload` hemen eklenmemelidir.
- Alt domainlerde HTTP kullanan eski sistemler varsa `includeSubDomains` sorun çıkarabilir.
- Production’a geçmeden önce staging/preview ortamlarında test edilmelidir.

Daha temkinli başlangıç:

```http
Strict-Transport-Security: max-age=31536000
```

## X-Content-Type-Options

```http
X-Content-Type-Options: nosniff
```

Tarayıcının dosya türünü tahmin etmeye çalışmasını engeller. Yanlış `Content-Type` ile servis edilen dosyaların beklenmeyen şekilde çalıştırılması riskini azaltır.

## X-Frame-Options ve frame-ancestors

```http
X-Frame-Options: DENY
```

Sayfanın başka bir sitede iframe/frame içinde gösterilmesini engeller ve clickjacking riskini azaltmaya yardımcı olur.

Modern CSP karşılığı:

```http
Content-Security-Policy: frame-ancestors 'none'
```

Eski tarayıcı uyumluluğu için `X-Frame-Options: DENY` pratik bir ek savunma katmanı olabilir.

## Referrer-Policy

```http
Referrer-Policy: strict-origin-when-cross-origin
```

Referrer bilgisinin karşı sitelere ne kadar gönderileceğini sınırlar. Genellikle iyi bir dengedir.

Daha sıkı yaklaşım:

```http
Referrer-Policy: no-referrer
```

Bu bazı analytics ve yönlendirme ölçümlerini etkileyebilir.

## Permissions-Policy

```http
Permissions-Policy: camera=(), microphone=(), geolocation=(), payment=(), usb=()
```

Tarayıcı özelliklerinin sayfa tarafından kullanılıp kullanılamayacağını sınırlar. Statik portfolyo, blog, landing page veya dokümantasyon sitelerinde kamera, mikrofon, konum, ödeme ve USB gibi izinlere çoğu zaman gerek yoktur.

Proje bu özelliklerden birini gerçekten kullanıyorsa, policy bilinçli şekilde dar kapsamlı güncellenmelidir.

## Content Security Policy

CSP, tarayıcıya hangi kaynakların güvenilir olduğunu söyleyen en kritik güvenlik header’larından biridir.

Başlangıç policy’si:

```http
Content-Security-Policy: default-src 'self'; object-src 'none'; base-uri 'self'; frame-ancestors 'none'; form-action 'self'; img-src 'self' data: https:; font-src 'self' data:; style-src 'self' 'unsafe-inline'; script-src 'self'; connect-src 'self'; upgrade-insecure-requests
```

Bu policy şunları hedefler:

- Varsayılan kaynakları aynı origin ile sınırlar.
- Eski plugin/object kullanımını kapatır.
- Sayfanın başka siteler içinde embed edilmesini engeller.
- Form gönderimlerini aynı origin ile sınırlar.
- Görseller için aynı origin, data URI ve HTTPS kaynaklara izin verir.
- Fontları self-hosted kullanmaya teşvik eder.
- Script kaynaklarını aynı origin ile sınırlar.
- HTTP kaynaklarını HTTPS’e yükseltmeye çalışır.

## CSP neden dikkatli uygulanmalı?

CSP güçlüdür ama yanlış uygulanırsa siteyi bozabilir.

Kırılabilecek alanlar:

- Google Fonts
- Analytics script’leri
- YouTube/Vimeo embed
- Harita embed
- Chat widget
- Ödeme sağlayıcısı
- Harici API endpoint’leri
- Inline script veya inline style kullanan eski component’ler

CSP önce production’a doğrudan sert şekilde uygulanmamalı; preview/staging ortamında test edilmelidir.

## Daha sıkı CSP hedefi

İleri seviye hedef:

```http
Content-Security-Policy: default-src 'self'; object-src 'none'; base-uri 'self'; frame-ancestors 'none'; form-action 'self'; img-src 'self' data: https:; font-src 'self'; style-src 'self'; script-src 'self'; connect-src 'self'; upgrade-insecure-requests
```

Bu daha sıkıdır; ancak her projede doğrudan çalışmayabilir.

Öneri:

1. Önce baseline CSP ile başla.
2. Harici kaynakları tek tek belirle.
3. Fontları self-hosted yap.
4. Gereksiz üçüncü parti scriptleri kaldır.
5. Inline style/script ihtiyacını azalt.
6. Sonra CSP’yi kademeli olarak sıkılaştır.

## Üçüncü parti script kontrolü

Yayın öncesi şu soruları sor:

- Bu script gerçekten gerekli mi?
- Hangi domain’den yükleniyor?
- Kullanıcı verisi topluyor mu?
- Analytics/tracking yapıyor mu?
- Privacy metninde bu akış açıklanıyor mu?
- Script compromise olursa siteyi etkiler mi?
- Alternatifi self-hosted veya daha dar kapsamlı olabilir mi?

Kural: Gerekçesi yazılamayan üçüncü parti script production’a alınmamalıdır.

## Font ve CDN bağımlılığı

AI ile üretilen sitelerde fontlar çoğu zaman doğrudan CDN’den çağrılır. Bu hızlıdır; ancak performans, privacy ve veri akışı açısından değerlendirilmelidir.

Sorular:

- Font kaynağı üçüncü taraf mı?
- Kullanıcı tarayıcısı bu üçüncü tarafa istek atıyor mu?
- CLS/layout shift yaratıyor mu?
- Self-hosted font kullanımı mümkün mü?

Öneri: Mümkünse production projelerinde fontları self-hosted kullan.

## Vercel için örnek

Örnek `vercel.json` için `examples/vercel-security-headers.json` dosyasına bakın. Bu örnek başlangıç içindir; her projeye körlemesine kopyalanmamalıdır.

## Production öncesi kontrol soruları

- [ ] Site sadece HTTPS üzerinden çalışıyor mu?
- [ ] HTTP → HTTPS yönlendirmesi doğru mu?
- [ ] HSTS production ortamında test edildi mi?
- [ ] CSP preview ortamında test edildi mi?
- [ ] Console’da CSP violation hataları kontrol edildi mi?
- [ ] Gereksiz üçüncü parti scriptler kaldırıldı mı?
- [ ] Font kaynakları gözden geçirildi mi?
- [ ] Analytics/tracking scriptleri gerçekten gerekli mi?
- [ ] Privacy metni gerçek veri akışıyla uyumlu mu?
- [ ] Form varsa hangi verinin nereye gittiği açık mı?
- [ ] `X-Content-Type-Options: nosniff` aktif mi?
- [ ] `frame-ancestors` veya `X-Frame-Options` ile clickjacking riski azaltıldı mı?
- [ ] Gereksiz tarayıcı izinleri `Permissions-Policy` ile kapatıldı mı?

## Ne yapılmamalı?

- Security headers ekleyip siteyi “tam güvenli” diye pazarlama.
- CSP’yi test etmeden production’a sert şekilde alma.
- Her hatayı `unsafe-inline` veya `*` ekleyerek çözme.
- Üçüncü parti scriptleri gerekçesiz ekleme.
- Font, analytics veya embed kaynaklarını “zararsız” varsayma.
- Kullanıcı verisi toplanıyorsa bunu gizlilik metninde açıklamadan yayınlama.
