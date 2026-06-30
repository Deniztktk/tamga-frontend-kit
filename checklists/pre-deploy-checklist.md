# Pre-Deploy Checklist

Bu checklist, AI destekli frontend projelerinde yayına çıkmadan önce temel kalite, erişilebilirlik, performans, güvenlik ve gizlilik kontrollerini hatırlatmak için hazırlanmıştır.

Bu liste tek başına güvenlik garantisi vermez; ancak “güzel görünüyor, o halde yayına alalım” refleksini azaltır.


Ayrıntılı kontroller için ilgili dosyalar:

- Security headers: `docs/security-headers.md`
- Deployment ortamı: `docs/deployment-hardening.md`
- AI stop koşulları: `rules/ai-stop-rules.md`


## 1. Build ve temel çalışma kontrolü

- [ ] Production build başarıyla tamamlanıyor.
- [ ] TypeScript hatası yok.
- [ ] Lint kontrolü geçti.
- [ ] Format kontrolü geçti.
- [ ] Console’da hata veya uyarı yok.
- [ ] Kullanılmayan import, component ve dosyalar temizlendi.
- [ ] 404/hata sayfaları beklenen şekilde çalışıyor.

## 2. UI ve responsive kontrol

- [ ] Mobil, tablet ve desktop görünüm kontrol edildi.
- [ ] Hero, CTA, navigation ve footer küçük ekranlarda bozulmuyor.
- [ ] Yatay overflow yok.
- [ ] Uzun metinler kartları veya layout’u kırmıyor.
- [ ] Görseller optimize edildi.
- [ ] Hover/focus states tutarlı.
- [ ] Tasarım sistemi dışı rastgele renk/font/spacing yok.

## 3. Accessibility kontrolü

- [ ] Tıklanabilir elementler doğru semantikle yazıldı: `button` veya `a`.
- [ ] Icon-only butonlarda `aria-label` var.
- [ ] Form input’larında label var.
- [ ] Klavye ile gezilebilirlik bozulmuyor.
- [ ] Focus state görünür.
- [ ] Renk kontrastı okunabilir.
- [ ] Animasyonlar rahatsız edici değil; gerekiyorsa reduced-motion dikkate alınıyor.

## 4. Performans kontrolü

- [ ] Lighthouse veya benzeri araçla temel performans kontrolü yapıldı.
- [ ] Büyük görseller sıkıştırıldı.
- [ ] Gereksiz video/animasyon yok.
- [ ] Font yükleme stratejisi CLS yaratmıyor.
- [ ] Lazy loading gereken medya doğrudan yüklenmiyor.
- [ ] Gereksiz client-side render veya ağır state yönetimi yok.

## 5. Dependency kontrolü

- [ ] Yeni eklenen paketlerin neden gerekli olduğu biliniyor.
- [ ] `npm audit` veya eşdeğer güvenlik kontrolü çalıştırıldı.
- [ ] `npm outdated` veya eşdeğer güncellik kontrolü yapıldı.
- [ ] Kullanılmayan paketler kaldırıldı.
- [ ] Tek bir küçük özellik için büyük dependency eklenmedi.
- [ ] Bakımı belirsiz paketler gözden geçirildi.

## 6. Üçüncü parti script kontrolü

- [ ] Harici scriptler listelendi.
- [ ] Her scriptin neden gerekli olduğu yazılabilir.
- [ ] Analytics/tracking davranışı biliniyor.
- [ ] Chat widget, embed, map, video veya ödeme scriptleri gerekiyorsa CSP’ye bilinçli eklendi.
- [ ] Gereksiz üçüncü parti scriptler kaldırıldı.
- [ ] Privacy metni gerçek veri akışıyla çelişmiyor.

## 7. Font/CDN kontrolü

- [ ] Fontlar self-hosted mı, üçüncü parti CDN’den mi geliyor?
- [ ] CDN kullanılıyorsa performans ve privacy etkisi değerlendirildi.
- [ ] Font yükleme stratejisi layout shift yaratmıyor.
- [ ] Gereksiz font weight’leri yüklenmiyor.

## 8. Security headers kontrolü

- [ ] HSTS production ortamına uygun.
- [ ] `X-Content-Type-Options: nosniff` aktif.
- [ ] `X-Frame-Options` veya `frame-ancestors` ile clickjacking riski azaltıldı.
- [ ] `Referrer-Policy` tanımlı.
- [ ] `Permissions-Policy` gereksiz tarayıcı izinlerini kapatıyor.
- [ ] CSP tanımlı veya bilinçli olarak sonraki aşamaya bırakıldı.
- [ ] CSP preview ortamında test edildi.
- [ ] CSP hataları `*` veya kontrolsüz `unsafe-inline` eklenerek çözülmedi.

## 9. Form, veri ve privacy kontrolü

- [ ] Form varsa hangi veri toplandığı açık.
- [ ] Veri nereye gidiyor biliniyor.
- [ ] Hata loglarında kişisel veri tutulmuyor.
- [ ] Gereksiz form alanı yok.
- [ ] Kullanıcıya veri akışı açıkça anlatılıyor.
- [ ] “Local-only”, “zero data”, “anonymous” gibi iddialar gerçek mimariyle uyumlu.

## 10. Environment ve secret kontrolü

- [ ] `.env` dosyaları Git’e eklenmedi.
- [ ] Sadece `.env.example` paylaşıldı.
- [ ] Client bundle içine secret girmiyor.
- [ ] Public environment variable’lar gerçekten public olabilir.
- [ ] API key, token, webhook secret veya private key repo içinde yok.

## 11. Deployment preview review

- [ ] Preview URL farklı cihazlarda açıldı.
- [ ] Production domain doğru deployment’a bağlı.
- [ ] HTTP → HTTPS yönlendirmesi çalışıyor.
- [ ] Header’lar canlı ortamda kontrol edildi.
- [ ] Preview ortamında kalmaması gereken debug/test içerikleri yok.
- [ ] Analytics/tracking yalnızca istenen ortamda aktif.

## 12. Son manuel kalite soruları

- [ ] Bu site ilk 5 saniyede ne yaptığını anlatıyor mu?
- [ ] AI template gibi görünen bölüm kaldı mı?
- [ ] Her section gerçekten gerekli mi?
- [ ] Gereksiz dependency var mı?
- [ ] Güvenlik veya privacy iddiası abartılı mı?
- [ ] Kullanıcı verisiyle ilgili belirsiz bir nokta var mı?
- [ ] Yayına almak için kendime güveniyor muyum, yoksa önce test etmem gereken bir şey var mı?
