# AI Stop Rules

Bu dosya, AI destekli frontend geliştirme sırasında modelin hangi durumlarda durması, kullanıcıyı uyarması veya daha güvenli alternatif önermesi gerektiğini tanımlar.

Amaç AI’ı yavaşlatmak değil; kontrolsüz değişiklikleri, güvenlik zayıflamalarını, tasarım tutarsızlıklarını ve gereksiz karmaşıklığı azaltmaktır.

## Ana prensip

AI şu durumda devam etmemelidir:

> Eğer değişiklik tasarım sistemini, güvenlik sınırlarını, erişilebilirliği, dependency sağlığını, gizlilik iddialarını veya deployment davranışını etkiliyorsa ve bu etki açıkça anlaşılmıyorsa, AI önce durmalı ve riski açıklamalıdır.

AI’ın görevi sadece kod üretmek değil; gerektiğinde “bu değişiklik riskli olabilir” diyebilmektir.

## 1. Tasarım sistemi bozuluyorsa dur

AI aşağıdaki durumlarda durmalı veya kullanıcıyı uyarmalıdır:

- Mevcut renk paleti dışına çıkıyorsa
- Rastgele gradient, gölge, neon veya hazır template hissi ekliyorsa
- Font sistemini değiştiriyorsa
- Spacing scale dışına çıkıyorsa
- Border radius hiyerarşisini bozuyorsa
- Aynı UI pattern için birden fazla tutarsız çözüm üretiyorsa
- Tasarım sistemi yerine sayfa bazlı rastgele Tailwind class’ları yığıyorsa

AI devam etmeden önce hangi kuralın etkilendiğini, değişikliğin neden gerekli olduğunu ve daha tutarlı alternatifin olup olmadığını açıklamalıdır.

## 2. Gereksiz dependency ekliyorsa dur

AI aşağıdaki durumlarda yeni paket eklememelidir:

- Aynı iş mevcut dependency veya basit yerel kod ile yapılabiliyorsa
- Paket bakım durumu bilinmiyorsa
- Paket küçük bir yardımcı fonksiyon için gereksiz büyükse
- Paket runtime güvenliği veya performansı etkileyebilecekse
- Paket üçüncü parti servis, analytics veya tracking davranışı ekliyorsa
- Kullanıcıdan açık onay alınmamışsa

Yeni dependency gerekiyorsa AI önce şunları yazmalıdır:

- Paket adı
- Neden gerekli olduğu
- Alternatifsiz olup olmadığı
- Bundle/performance etkisi
- Security/privacy etkisi
- Kaldırılması gerekirse hangi dosyaları etkileyeceği

## 3. Güvenlik ayarlarını gevşetiyorsa dur

AI aşağıdaki değişiklikleri kullanıcı onayı olmadan yapmamalıdır:

- CSP’yi genişletmek
- `script-src` içine `*`, `unsafe-inline` veya kontrolsüz harici domain eklemek
- Security headers’ı kaldırmak
- HSTS ayarlarını değiştirmek
- Permissions-Policy izinlerini genişletmek
- Harici script, iframe, embed veya widget eklemek
- Debug endpoint, test route veya admin benzeri yapı eklemek
- Environment variable veya secret değerlerini görünür hale getirmek

AI önce bu değişikliğin neden gerekli olduğunu, hangi riski doğurabileceğini ve daha dar kapsamlı alternatifin olup olmadığını değerlendirmelidir.

## 4. Gizlilik veya veri akışı değişiyorsa dur

AI aşağıdaki durumlarda devam etmemelidir:

- Yeni form alanı ekleniyorsa
- Kullanıcı verisi toplanıyorsa
- Analytics veya tracking script’i ekleniyorsa
- Üçüncü parti servise kullanıcı verisi gidebilecekse
- Local-only, privacy-first veya “veri toplanmaz” gibi iddialar etkileniyorsa
- Kullanıcı içeriği, mesajı, e-postası veya kişisel bilgisi işleniyorsa

AI önce şu soruları cevaplamalıdır:

- Hangi veri toplanıyor?
- Veri nereye gidiyor?
- Veri ne kadar süre tutuluyor?
- Kullanıcıya bu açıkça söyleniyor mu?
- Mevcut gizlilik iddialarıyla çelişiyor mu?

## 5. Accessibility zayıflıyorsa dur

AI aşağıdaki durumlarda durmalıdır:

- Buton yerine tıklanabilir `div` kullanıyorsa
- Link ve buton davranışlarını karıştırıyorsa
- `aria-label` gerektiren ikon butonlar etiketsiz kalıyorsa
- Focus state kaldırılıyorsa
- Klavye navigasyonu bozuluyorsa
- Renk kontrastı düşüyorsa
- Animasyonlar `prefers-reduced-motion` dikkate almıyorsa
- Form alanları label olmadan ekleniyorsa

AI görsel kaliteyi erişilebilirlik pahasına artırmamalıdır.

## 6. Performans veya kullanıcı hissi bozuluyorsa dur

AI aşağıdaki durumlarda kullanıcıyı uyarmalıdır:

- Gereksiz büyük animasyonlar ekliyorsa
- Scroll event listener’ları kontrolsüz çoğalıyorsa
- Büyük görseller optimize edilmeden kullanılıyorsa
- Font yükleme stratejisi CLS yaratabilecekse
- Lazy loading gerektiren medya doğrudan yükleniyorsa
- Gereksiz client-side state veya render döngüsü oluşuyorsa
- Mobil performans test edilmeden ağır motion ekleniyorsa

Premium his, ağır animasyon demek değildir.

## 7. İçerik veya iddia abartılıysa dur

AI aşağıdaki ifadeleri üretmemelidir:

- “%100 güvenli”
- “Tam güvenli”
- “Kusursuz koruma”
- “KVKK uyumlu” — hukuki/teknik inceleme yoksa
- “Sıfır veri toplama” — gerçek veri akışı doğrulanmadıysa
- “Tamamen anonim” — teknik olarak kanıtlanmadıysa
- “Hacklenemez”
- “Kurumsal seviye güvenlik” — kapsam tanımlı değilse

AI iddia üretmeden önce bu iddianın teknik olarak doğru olup olmadığını ve kod/mimariyle desteklenip desteklenmediğini kontrol etmelidir.

## 8. Scope drift oluşuyorsa dur

AI aşağıdaki durumlarda görevi genişletmemelidir:

- Kullanıcı sadece UI isterken backend eklemek
- Statik siteye auth sistemi eklemek
- Basit form yerine veritabanı kurmak
- Landing page’e gereksiz dashboard eklemek
- Tasarım revizyonu isterken tüm mimariyi değiştirmek
- Küçük düzeltme isterken komple yeniden yazmak

AI önce daha küçük ve güvenli bir alternatif önermelidir.

## 9. Test veya doğrulama yapılmadan “bitti” demeyi durdur

AI şu kontroller yapılmadan işi tamamlanmış gibi sunmamalıdır:

- Build çalışıyor mu?
- TypeScript hatası var mı?
- Lint/format kontrolü geçti mi?
- Responsive görünüm kontrol edildi mi?
- Temel accessibility kontrolü yapıldı mı?
- Console error var mı?
- Gereksiz dependency eklendi mi?
- Security/privacy etkisi var mı?
- Kullanılmayan kod kaldı mı?

AI test çalıştıramıyorsa bunu açıkça söylemelidir.

## 10. AI’ın durduğunda kullanacağı cevap formatı

```txt
Durdum çünkü bu değişiklik şu alanı etkiliyor:
[design / security / privacy / accessibility / performance / dependency / deployment]

Risk:
[Kısa açıklama]

Neden önemli:
[Kullanıcı veya proje açısından etkisi]

Daha güvenli alternatif:
[Önerilen çözüm]

Devam etmek için:
[Onay gereken karar veya yapılacak kontrol]
```

## Kısa özet

Bu dosyanın amacı AI’ı pasifleştirmek değil; AI’ın daha iyi bir teknik ekip arkadaşı gibi davranmasını sağlamaktır.

İyi bir AI workflow:

- Ne zaman duracağını bilir.
- Gereksiz dependency eklemez.
- Tasarım sistemini bozmaz.
- Güvenlik ayarlarını rastgele gevşetmez.
- Privacy iddialarını abartmaz.
- Accessibility’i görmezden gelmez.
- Test etmeden “bitti” demez.
