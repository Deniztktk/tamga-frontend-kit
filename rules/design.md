# Design Rules

Bu dosya, AI destekli frontend üretiminde kullanılabilecek tasarım sistemi kurallarını tanımlar. Amaç AI’a “güzel site yap” demek yerine; görsel yön, spacing, tipografi, motion ve component davranışını net sınırlarla vermektir.

Bu dosyayı kendi projenin marka dili, renkleri ve hedef kitlesine göre düzenleyerek kullan.

## 1. Görsel yön

Tasarım şu hissi vermelidir:

- Temiz
- Güvenilir
- Odaklı
- Fazla süslenmemiş
- Jenerik SaaS template gibi görünmeyen
- Teknik ama soğuk olmayan
- Modern ama klişe olmayan

Kaçınılacak his:

- Hacker yeşili / matrix / terminal klişesi
- Rastgele mor-mavi gradient
- Gereksiz cam efekti
- Her yerde glow/shadow kullanımı
- Her component’in farklı dünyadan gelmesi

## 2. Renk sistemi

Renk paleti sınırlı tutulmalıdır.

Öneri:

- 1 ana arka plan rengi
- 1 ana metin rengi
- 1 ikincil metin rengi
- 1 border rengi
- 1 accent rengi

Kural:

- Yeni renk eklemeden önce mevcut palette karşılığı var mı kontrol et.
- Accent rengi her yerde kullanılmamalı; yalnızca yönlendirme, vurgu veya imza öğesinde kullanılmalı.
- Renkler accessibility kontrastını bozmayacak şekilde seçilmeli.

## 3. Tipografi

Tipografi, sitenin profesyonel hissinin ana taşıyıcısıdır.

Kural:

- En fazla 2 font ailesi kullan.
- Başlık ve gövde fontları bilinçli eşleşmeli.
- Başlıklar yeterli kontrast ve hiyerarşi oluşturmalı.
- Küçük label, badge veya teknik metinlerde mono font kullanılabilir.
- Her section aynı başlık boyutunu kullanmamalı; ritim ve hiyerarşi olmalı.

Yasak:

- Rastgele Google Fonts denemeleri
- Her bölümde farklı font hissi
- Okunabilirliği düşüren aşırı dekoratif fontlar

## 4. Spacing

Spacing tutarlılığı için 4px veya 8px tabanlı scale kullanılmalıdır.

Kural:

- Component içi boşluklar küçük scale ile yönetilmeli.
- Section arası boşluklar daha büyük ve bilinçli olmalı.
- Sıkışık tasarım, “daha fazla içerik” uğruna tercih edilmemeli.
- Gereksiz boşluk da kullanılmamalı; her boşluğun ritim amacı olmalı.

## 5. Border radius

Border radius bir stil kararıdır; rastgele verilmemelidir.

Örnek hiyerarşi:

- Küçük elementler: `rounded-sm` veya `rounded-md`
- Kartlar: `rounded-xl`
- Büyük surface: `rounded-2xl` veya `rounded-3xl`
- Brutalist/editorial yön varsa: keskin köşeler veya çok düşük radius

Kural:

Aynı tasarım içinde hem aşırı yuvarlak hem keskin komponentler bilinçsizce karıştırılmamalı.

## 6. Grid ve layout

Layout yalnızca ortalanmış hero + üç kart düzeninden ibaret olmamalıdır.

Kural:

- Section’lar arasında ritim değişimi olmalı.
- Gerektiğinde asimetrik grid kullanılabilir.
- Mobilde içerik sırası anlamlı kalmalı.
- CTA, açıklama ve görsel öğeler aynı hiyerarşiyi paylaşmamalı.

İyi layout soruları:

- Kullanıcı ilk 5 saniyede neyi anlamalı?
- En önemli cümle gerçekten en görünür yerde mi?
- Boşluklar içeriği güçlendiriyor mu?
- Mobilde aynı etki korunuyor mu?

## 7. Motion kuralları

Motion, anlamı güçlendirmek için kullanılmalıdır.

Kural:

- Her şeyi animasyonlu yapma.
- Bir sayfada 1 ana imza motion öğesi yeterli olabilir.
- Scroll reveal sade ve tutarlı olmalı.
- Hover efektleri hızlı, sakin ve erişilebilir olmalı.
- `prefers-reduced-motion` dikkate alınmalı.
- Mobil performans test edilmeden ağır animasyon eklenmemeli.

Yasak:

- Sonsuz dönen gereksiz animasyonlar
- Dikkat dağıtan parallax kullanımı
- Tıklama ve okuma davranışını zorlaştıran motion
- Premium his için ağır animasyon kullanmak

## 8. Hover ve focus states

Hover yalnızca görsel süs değildir; etkileşimi anlaşılır kılmalıdır.

Kural:

- Tıklanabilir her elementin hover/focus state’i olmalı.
- Focus ring kaldırılmamalı; tasarıma uygun hale getirilmeli.
- İkon butonlarda erişilebilir label olmalı.
- Hover efektleri layout shift yaratmamalı.

## 9. Yasaklanan AI template alışkanlıkları

AI aşağıdaki pattern’leri gerekçesiz üretmemelidir:

- Ortada büyük gradient hero
- Altında üç feature card
- Her kartta aynı icon + başlık + açıklama düzeni
- Mor/mavi glow background
- “Unlock the future” gibi boş pazarlama cümleleri
- Rastgele testimonial section
- Gereksiz pricing table
- Her yere `rounded-2xl shadow-xl`
- Aynı sayfada birden fazla farklı button stili
- Tasarım sistemi dışında rastgele renkler

## 10. Accessibility notları

- Renk kontrastı kontrol edilmeli.
- Buton ve link semantiği doğru kullanılmalı.
- Klavye navigasyonu bozulmamalı.
- Form alanlarında label olmalı.
- İkon-only butonlarda `aria-label` olmalı.
- Animasyonlar azaltılmış hareket tercihine saygı göstermeli.

## 11. AI çıktısı gibi görünmemesi için kontrol listesi

- [ ] Sayfanın tek bir imza öğesi var mı?
- [ ] Renk paleti sınırlı ve tutarlı mı?
- [ ] Tipografi hiyerarşisi belirgin mi?
- [ ] Her section aynı layout kalıbını tekrar etmiyor mu?
- [ ] Kartlar ve butonlar aynı component sisteminden geliyor mu?
- [ ] Motion anlamlı ve ölçülü mü?
- [ ] Hover/focus states tutarlı mı?
- [ ] Gereksiz gradient, glow veya shadow kaldırıldı mı?
- [ ] Mobil görünüm özenli mi?
- [ ] Accessibility temel kontrolleri yapıldı mı?
