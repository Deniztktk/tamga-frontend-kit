# Premium Hero Prompt

Bu prompt, AI’a jenerik hero section üretmek yerine karakterli, akılda kalan ve tasarım felsefesini görselleştiren bir hero section tasarlatmak için hazırlanmıştır.

Amaç daha fazla efekt değil; daha net bir konsepttir.

## Kullanım notu

Bu prompt’u kendi proje bağlamına göre düzenle. Marka adı, slogan, renk, font ve hedef kitle bilgilerini değiştirmeden doğrudan kullanma.

## Prompt

```txt
Sen deneyimli bir frontend designer ve motion-aware React geliştiricisisin.

Bana jenerik SaaS template gibi görünmeyen, karakterli ve profesyonel bir hero section tasarla.

Proje bağlamı:
- Kişisel / profesyonel web sitesi
- Alan: siber güvenlik, güvenli web tasarım, açık kaynak dijital güvenlik araştırmaları
- Hedef his: ciddi, editorial, güvenilir, teknik ama klişe hacker estetiği olmayan

Ana slogan:
“Sistemlerin en büyük zafiyeti insan faktörüdür.”

İmza öğesi:
- “insan” kelimesi hero’nun görsel imza öğesi olsun.
- Bu kelime insan faktörünün kırılganlığını temsil etmeli.
- Harfler çok hafif şekilde titreyen/kayan bir motion detayına sahip olabilir.
- Motion abartılı olmamalı; okuma deneyimini bozmamalı.
- Hover’da harfler çok hafif ayrışabilir ama layout kırılmamalı.
- `prefers-reduced-motion` dikkate alınmalı.

Görsel yön:
- Editorial, sade, güçlü tipografi.
- Gereksiz 3D obje, hologram, neon hacker estetiği, matrix efekti yok.
- Renk paleti sınırlı: açık/koyu nötrler + tek accent rengi.
- Her yerde gradient, glow veya shadow kullanma.
- Bir tane güçlü fikir yeterli: “insan” kelimesi.

Layout:
- Devasa tipografiyle güçlü giriş.
- Alt açıklama: “Güvenlik sonradan eklenmez, baştan inşa edilir.”
- Küçük label: “Red Team · Siber Güvenlik Analisti”
- CTA butonları sade ve erişilebilir olmalı.
- Mobil görünüm ayrıca düşünülmeli.

Teknik kurallar:
- React + TypeScript ile yaz.
- Tailwind CSS kullan.
- Motion için mevcut proje kütüphanesini kullan; gereksiz dependency ekleme.
- Semantik HTML kullan.
- Buton/link ayrımını doğru yap.
- Accessibility’i bozma.
- Kullanılmayan kod bırakma.

Yasaklar:
- Generic three-card feature section üretme.
- Mor/mavi random gradient hero yapma.
- “AI”, “future”, “unlock”, “next generation” gibi boş pazarlama dili kullanma.
- Her component’e shadow/glow ekleme.
- Sadece güzel görünsün diye ağır animasyon yazma.

Çıktı formatı:
1. Önce kısa tasarım gerekçesini yaz.
2. Sonra component kodunu ver.
3. Sonra responsive ve accessibility notlarını yaz.
4. Son olarak hangi dosyalara eklenmesi gerektiğini belirt.
```

## Neden bu prompt daha iyi çalışır?

Bu prompt AI’a yalnızca “güzel hero yap” demez. Şunları netleştirir:

- Tek bir imza öğesi
- Görsel felsefe
- Yasaklanan klişeler
- Motion sınırı
- Accessibility beklentisi
- Teknik stack
- Çıktı formatı

Jenerik promptlar ortalama sonuç üretir. İyi prompt ise AI’ın karar alanını daraltır ve tasarım yönünü netleştirir.
