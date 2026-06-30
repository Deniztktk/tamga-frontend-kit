# Recommended Stack

Bu dosya, AI destekli frontend üretiminde kullanılabilecek pratik ve sade bir başlangıç stack’i önerir. Amaç “tek doğru teknoloji” ilan etmek değil; vibe coding hızını kaybetmeden daha kontrollü, okunabilir, erişilebilir ve yayına hazırlanabilir bir yapı kurmaktır.

## 1. Proje iskeleti: Vite + React + TypeScript

**Ne sağlar?** Hızlı geliştirme ortamı, modern React kullanımı ve tip güvenliği.

**Neden profesyonel hissi artırır?** Çünkü AI’ın ürettiği kod büyüdükçe tip kontrolü, bileşen sınırları ve dosya yapısı daha önemli hale gelir. TypeScript, modelin yanlış prop kullanımı, eksik veri yapısı veya belirsiz component ilişkileri üretmesini daha erken görünür yapar.

Örnek başlangıç:

```bash
npm create vite@latest my-site -- --template react-ts
```

## 2. Stil sistemi: Tailwind CSS

**Ne sağlar?** Utility-first CSS yaklaşımıyla hızlı ama kontrollü stil üretimi.

**Neden profesyonel hissi artırır?** Tailwind, tasarım token’ları doğru tanımlandığında spacing, renk, responsive davranış ve component tutarlılığını kod içinde yaşatır. Ancak kontrolsüz kullanılırsa class karmaşasına dönüşür. Bu yüzden Tailwind mutlaka `design.md` ve component kurallarıyla birlikte kullanılmalıdır.

## 3. Component sistemi: shadcn/ui

**Ne sağlar?** Tailwind ve Radix UI tabanlı, kopyalanabilir ve özelleştirilebilir component altyapısı.

**Neden profesyonel hissi artırır?** AI’ın her sayfada farklı buton, dialog, card veya form pattern’i üretmesini azaltır. Component’ler proje koduna geldiği için tasarım ve davranış tamamen özelleştirilebilir kalır.

Örnek başlangıç:

```bash
npx shadcn@latest init
```

## 4. İkon sistemi: Lucide React

**Ne sağlar?** Tutarlı stroke yapısına sahip, hafif ve modern ikon seti.

**Neden profesyonel hissi artırır?** AI çıktılarında ikonlar genelde rastgele seçilir. Lucide gibi tek bir ikon sistemi kullanmak görsel dili toparlar.

```bash
npm install lucide-react
```

## 5. Motion katmanı: Motion / Framer Motion yaklaşımı

**Ne sağlar?** React component’leri içinde deklaratif animasyon ve geçiş yönetimi.

**Neden profesyonel hissi artırır?** Premium his, her şeyi hareket ettirmekle değil; doğru yerde, ölçülü ve anlamlı hareket kullanmakla oluşur. Motion; hover, reveal, layout transition ve mikro etkileşimleri daha okunabilir şekilde yönetmeye yardımcı olur.

```bash
npm install motion
```

Not: Bazı projelerde hâlâ `framer-motion` kullanımı görülebilir. Yeni proje başlatırken paket adını ve dokümantasyonu güncel kontrol etmek gerekir.

## 6. Smooth scroll: Lenis

**Ne sağlar?** Scroll hissini daha kontrollü ve yumuşak hale getiren hafif smooth scroll katmanı.

**Neden profesyonel hissi artırır?** Scroll davranışı sitenin “ucuz template” ya da “özenilmiş ürün” gibi algılanmasında etkili olabilir. Ancak Lenis her projeye körlemesine eklenmemelidir. Mobil performans, erişilebilirlik ve `prefers-reduced-motion` davranışı mutlaka test edilmelidir.

```bash
npm install lenis
```

## 7. Font yönetimi: self-hosted fonts / Fontsource

**Ne sağlar?** Font dosyalarını daha kontrollü yükleme ve CDN bağımlılığını azaltma imkânı.

**Neden profesyonel hissi artırır?** Tipografi tasarımın büyük bölümünü taşır. Fontların geç yüklenmesi CLS, kötü ilk izlenim ve performans sorunları yaratabilir. Mümkün olduğunda WOFF2, subset ve `font-display: swap` stratejisi düşünülmelidir.

Örnek:

```bash
npm install @fontsource/inter @fontsource/space-grotesk
```

## 8. Routing: React Router

**Ne sağlar?** Çok sayfalı frontend yapısını yönetir.

**Neden profesyonel hissi artırır?** Portfolio, blog, araştırma, kaynak, hizmet ve iletişim gibi ayrı sayfaları tek component yığınına dönüştürmeden yönetmeyi sağlar.

```bash
npm install react-router
```

## 9. Kod kalitesi: Biome / ESLint

**Ne sağlar?** Formatlama, lint kontrolü ve tutarlı kod stili.

**Neden profesyonel hissi artırır?** AI ile uzun süre çalışıldığında kullanılmayan import’lar, tekrar eden component’ler, biçim tutarsızlıkları ve gereksiz karmaşa oluşabilir. Biome veya ESLint bu bozulmayı erken görünür yapar.

```bash
npm install --save-dev --save-exact @biomejs/biome
```

## 10. Deployment preview: Vercel

**Ne sağlar?** Git tabanlı preview ve production deployment akışı.

**Neden profesyonel hissi artırır?** Her değişiklik gerçek cihazlarda, farklı ekranlarda ve canlı URL üzerinde test edilebilir. AI ile üretilen arayüzlerin yalnızca lokal ortamda güzel görünmesi yeterli değildir.

## 11. Premium component keşfi: 21st.dev

**Ne sağlar?** Daha kaliteli React/Tailwind component örnekleri ve AI araçlarıyla kullanılabilecek component keşif akışı.

**Neden profesyonel hissi artırır?** Jenerik component düzeninden çıkmak için hazır ama daha rafine UI pattern’leri incelemek faydalıdır. Yine de her component projeye körlemesine eklenmemeli; tasarım sistemi, accessibility ve dependency etkisi değerlendirilmelidir.

## 12. Referans ve tasarım pipeline: Figma → Code

**Ne sağlar?** AI’a doğrudan “güzel site yap” demek yerine önce görsel yön, layout, spacing, tipografi ve component mantığını belirlemeyi sağlar.

**Neden profesyonel hissi artırır?** AI çoğu zaman ortalama tasarım üretir. Figma’da referans analizi ve tasarım sistemi kararı yapılmadan koda geçmek, jenerik sonuç ihtimalini artırır.

## Vite mi Next.js mi?

Bu repo, sade frontend workflow için varsayılan olarak **Vite + React + TypeScript** önerir.

Next.js şu durumlarda değerlendirilebilir:

- SSR/SSG ihtiyacı varsa
- İçerik yoğunluğu ve SEO kritikse
- MDX/blog altyapısı büyüyorsa
- Auth, API route veya server tarafı ihtiyaçları varsa
- Görsel optimizasyon, metadata ve route-level rendering stratejileri önemliyse

Kısa karar:

- Küçük landing page, kişisel site, demo, statik rehber: Vite iyi başlangıçtır.
- İçerik, SEO, backend ve server tarafı büyüyorsa: Next.js düşünülebilir.

Amaç framework savaşı değil; proje bağlamına göre bilinçli seçim yapmaktır.
