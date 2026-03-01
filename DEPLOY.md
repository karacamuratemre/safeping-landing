# 🚀 SafePing Vercel Deployment Kılavuzu

## Yöntem 1: Vercel CLI (En Hızlı - 2 Dakika)

### Adım 1: Vercel CLI Kur
```bash
npm install -g vercel
```

### Adım 2: Proje Klasörüne Git
```bash
cd safeping-landing
```

### Adım 3: Deploy Et
```bash
vercel
```

### Adım 4: Soruları Cevapla
```
? Set up and deploy? Y
? Which scope? (Hesabını seç)
? Link to existing project? N
? Project name? safeping (veya safeping-landing)
? Directory? ./
? Override settings? N
```

### Adım 5: Production Deploy
```bash
vercel --prod
```

✅ **Sonuç:** `https://safeping.vercel.app` veya `https://safeping-landing.vercel.app`

---

## Yöntem 2: GitHub + Vercel (Önerilen - CI/CD)

### Adım 1: GitHub'a Yükle

```bash
# Git başlat
cd safeping-landing
git init
git add .
git commit -m "Initial commit: SafePing landing page"

# GitHub repo oluştur (github.com'dan veya CLI ile)
gh repo create safeping-landing --public

# Push et
git branch -M main
git remote add origin https://github.com/KULLANICI_ADIN/safeping-landing.git
git push -u origin main
```

### Adım 2: Vercel'e Bağla

1. [vercel.com](https://vercel.com) → **Login**
2. **Add New** → **Project**
3. **Import Git Repository** → GitHub'ı bağla
4. `safeping-landing` repo'yu seç
5. **Deploy** tıkla

### Adım 3: Custom Domain (Opsiyonel)

1. Vercel Dashboard → Proje → **Settings** → **Domains**
2. `safeping.app` veya istediğin domaini ekle
3. DNS ayarlarını yap:
   - **A Record:** `76.76.19.19`
   - **CNAME:** `cname.vercel-dns.com`

---

## Yöntem 3: Vercel Dashboard (Drag & Drop)

1. [vercel.com/new](https://vercel.com/new) → Login
2. **Upload** sekmesine tıkla
3. `public` klasörünü sürükle-bırak
4. **Deploy** tıkla

---

## 🔧 Ortam Değişkenleri (Opsiyonel)

Vercel Dashboard → Project → Settings → Environment Variables

```
# Örnek (şimdilik gerekli değil)
NEXT_PUBLIC_API_URL=https://api.safeping.app
```

---

## 📊 Analytics Ekleme (Opsiyonel)

### Vercel Analytics
```bash
# package.json'a ekle
npm install @vercel/analytics
```

### Google Analytics
`index.html` içine `</head>` öncesine ekle:
```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

---

## 🌐 Custom Domain Ayarları

### Namecheap
1. Domain List → Manage → Advanced DNS
2. Ekle:
   - Type: `A Record`, Host: `@`, Value: `76.76.19.19`
   - Type: `CNAME`, Host: `www`, Value: `cname.vercel-dns.com`

### Cloudflare
1. DNS → Add Record
2. Ekle:
   - Type: `A`, Name: `@`, Content: `76.76.19.19`, Proxy: OFF
   - Type: `CNAME`, Name: `www`, Content: `cname.vercel-dns.com`, Proxy: OFF

### GoDaddy
1. My Products → DNS → Manage
2. Ekle:
   - Type: `A`, Name: `@`, Value: `76.76.19.19`
   - Type: `CNAME`, Name: `www`, Value: `cname.vercel-dns.com`

---

## ✅ Checklist

- [ ] Vercel CLI kuruldu
- [ ] `vercel` komutu çalıştırıldı
- [ ] Production deploy yapıldı (`vercel --prod`)
- [ ] URL çalışıyor
- [ ] TR/EN dil değişimi çalışıyor
- [ ] Formlar çalışıyor
- [ ] Mobile responsive kontrol edildi
- [ ] Custom domain eklendi (opsiyonel)
- [ ] SSL aktif (Vercel otomatik yapar)

---

## 🐛 Sorun Giderme

### "Command not found: vercel"
```bash
npm install -g vercel
# veya
npx vercel
```

### "Not authorized"
```bash
vercel login
```

### "Build failed"
Bu statik site, build gerekmiyor. `vercel.json` doğru olduğundan emin ol.

### Sayfa 404 veriyor
`public/index.html` dosyasının mevcut olduğundan emin ol.

---

## 📞 Destek

Sorun yaşarsan:
- Vercel Docs: https://vercel.com/docs
- Vercel Status: https://vercel-status.com

---

🎉 **Tebrikler!** SafePing landing page canlıda!
