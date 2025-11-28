# 🚀 GitHub Actions ile Otomatik Build - Tüm Platformlar

## ✨ Özellikler

**Otomatik Build Sistemi:**
- ✅ Windows (Setup.exe + Portable.exe)
- ✅ macOS (DMG + ZIP)
- ✅ Linux (AppImage + DEB + RPM)
- ✅ Her commit'te otomatik build
- ✅ Release tag'lerinde otomatik yayınlama
- ✅ Manuel build tetikleme
- ✅ Hiçbir şey yüklemeden build!

---

## 🛠️ Kurulum (Tek Seferlik)

### 1. GitHub Repository Oluştur

1. GitHub.com'a git
2. "New Repository" oluştur
3. Repo adı: `whatgram` (veya istediğiniz ad)
4. Public veya Private seç

### 2. Kodu GitHub'a Yükle

```bash
cd /app
git init
git add .
git commit -m "Initial commit - WhatGram Desktop App"
git branch -M main
git remote add origin https://github.com/KULLANICI_ADINIZ/whatgram.git
git push -u origin main
```

### 3. GitHub Actions'u Aktifleştir

1. GitHub repo sayfanıza git
2. "Actions" tab'ine tıkla
3. "I understand my workflows, go ahead and enable them" butonuna tıkla

**🎉 Tamam! Artık otomatik build çalışıyor!**

---

## 🔄 Otomatik Build Senaryoları

### Senaryo 1: Her Commit'te Build

```bash
# Kod değişikliği yap
git add .
git commit -m "Feature: New awesome feature"
git push

# GitHub Actions otomatik başlar!
# 15-20 dakika sonra:
# - Windows .exe dosyaları
# - macOS .dmg dosyaları
# - Linux .AppImage dosyaları
# Artifacts olarak kaydedilir
```

### Senaryo 2: Release Yayınlama

```bash
# Version tag oluştur
git tag v1.0.0
git push origin v1.0.0

# GitHub Actions:
# 1. Tüm platformlar için build yapar
# 2. GitHub Release oluşturur
# 3. Tüm dosyaları release'e ekler
# 4. Kullanıcılar direkt indirebilir!
```

### Senaryo 3: Manuel Build

1. GitHub repo'nuza git
2. "Actions" tab
3. "Manual Build - All Platforms" seç
4. "Run workflow" butonuna tıkla
5. Version gir (1.0.0)
6. Platform seç (all/windows/macos/linux)
7. "Run workflow" tıkla

**15-20 dakika sonra dosyalar hazır!**

---

## 📦 Build Dosyalarını İndirme

### Method 1: Artifacts (Her Build)

1. GitHub repo > "Actions"
2. Son workflow run'u aç
3. Aşağıda "Artifacts" bölümü
4. İndirmek için tıkla:
   - `windows-build.zip`
   - `macos-build.zip`
   - `linux-build.zip`

### Method 2: Releases (Tag Build)

1. GitHub repo > "Releases"
2. Son release'i aç
3. "Assets" bölümünden indir:
   - `WhatGram-Setup-Windows.exe`
   - `WhatGram-Portable-Windows.exe`
   - `WhatGram-macOS.dmg`
   - `WhatGram-Linux.AppImage`

---

## 📊 Build Workflow Detayları

### Workflow 1: `build.yml` (Otomatik)

**Tetikleyiciler:**
- Push to `main` veya `master` branch
- Pull request
- Tag push (`v*`)

**İşlemler:**
1. Kod checkout
2. Node.js kurulum
3. Dependencies yükleme
4. React build
5. Electron build (platform'a göre)
6. Artifacts upload
7. Release oluşturma (tag varsa)

**Süre:** ~15-20 dakika

### Workflow 2: `manual-build.yml` (Manuel)

**Tetikleyici:**
- Manuel başlatma (workflow_dispatch)

**Parametreler:**
- `version`: Version numarası (1.0.0)
- `platform`: Hangi platform (all/windows/macos/linux)

**İşlemler:**
1. Version güncelleme
2. Build yapma
3. Artifacts upload

**Süre:** ~15-20 dakika (tüm platformlar için)

---

## 🔧 Konfigürasyon

### Backend URL Ayarlama

**Option 1: GitHub Secrets** (Güvenli)

1. GitHub repo > Settings > Secrets and variables > Actions
2. "New repository secret"
3. Name: `BACKEND_URL`
4. Value: `https://your-backend.com`
5. Save

**Option 2: .env Dosyası**

`/app/frontend/.env` dosyasını düzenle:
```env
REACT_APP_BACKEND_URL=https://your-backend.com
```

Commit ve push yap.

### Icon Dosyaları

Build'den önce icon ekle:

```bash
# Icon dosyalarını ekle
cp your-icon.ico /app/frontend/build-resources/icon.ico
cp your-icon.png /app/frontend/build-resources/icon.png

# Commit et
git add frontend/build-resources/
git commit -m "Add app icons"
git push
```

---

## 📢 Release Yayınlama Süreci

### Adım 1: Version Hazırla

```bash
# package.json'da version güncelle
cd /app/frontend
# version: "1.0.0" → "1.0.1"

git add package.json
git commit -m "Bump version to 1.0.1"
git push
```

### Adım 2: Tag Oluştur

```bash
git tag v1.0.1
git push origin v1.0.1
```

### Adım 3: GitHub Actions İzleme

1. GitHub > Actions
2. "Build WhatGram Desktop Apps" workflow'unu izle
3. Build tamamlanınca kontrol et

### Adım 4: Release Kontrol

1. GitHub > Releases
2. "v1.0.1" release'ini gör
3. Assets'i kontrol et:
   - ✅ WhatGram-Setup-Windows.exe
   - ✅ WhatGram-Portable-Windows.exe
   - ✅ WhatGram-macOS.dmg
   - ✅ WhatGram-Linux.AppImage

### Adım 5: Duyur

Release URL'ini paylaş:
```
https://github.com/KULLANICI_ADINIZ/whatgram/releases/tag/v1.0.1
```

---

## 🧑‍💻 Geliştirici Notları

### Workflow Loglarını İzleme

1. GitHub > Actions
2. Build workflow'u aç
3. Her job'u tıklayarak loglara bak
4. Hataları kontrol et

### Build Başarısız Olursa

**Yaygın hatalar:**

1. **Icon dosyası yok**
   - `build-resources/` klasörüne icon ekle

2. **Dependencies hatası**
   - `yarn.lock` dosyasını commit et

3. **Build hatası**
   - Loglarda detaylı hata mesajını oku
   - Local'de test et: `yarn build`

4. **Artifacts upload hatası**
   - Dosya yolu doğru mu kontrol et

### Local'de Test Etme

GitHub Actions'a göndermeden önce:

```bash
cd /app/frontend
yarn install
yarn build
# Hata varsa düzelt
```

---

## 📊 Build İstatistikleri

**Süreler:**
- Windows build: ~5-7 dakika
- macOS build: ~8-10 dakika
- Linux build: ~5-7 dakika
- **Toplam (paralel)**: ~15-20 dakika

**Dosya Boyutları:**
- Windows Setup: ~150-180 MB
- Windows Portable: ~150-180 MB
- macOS DMG: ~160-200 MB
- Linux AppImage: ~140-170 MB

**GitHub Actions Limitleri:**
- **Public repo**: Sınırsız dakika (bedava!)
- **Private repo**: 2,000 dakika/ay (bedava)
- Her build: ~15-20 dakika
- Aylık ~100 build yapabilirsiniz (private)

---

## ✅ Avantajlar

**GitHub Actions ile:**
- ✅ Hiçbir şey yüklemeden build
- ✅ Tüm platformlar paralel build
- ✅ Otomatik release yayınlama
- ✅ Public repo'da bedava
- ✅ Professional CI/CD
- ✅ Version kontrol entegrasyonu
- ✅ Artifacts otomatik saklanır (30 gün)

---

## 📝 Örnek Workflow Run

```bash
# 1. Kod değiştir
echo "New feature" >> /app/frontend/src/App.js

# 2. Commit et
git add .
git commit -m "feat: Add new feature"

# 3. Push et
git push origin main

# GitHub Actions otomatik başlar:
# - Windows build başladı...
# - macOS build başladı...
# - Linux build başladı...
#
# 15 dakika sonra:
# - ✅ Windows artifacts hazır
# - ✅ macOS artifacts hazır
# - ✅ Linux artifacts hazır
#
# GitHub > Actions > Artifacts'ten indir!
```

---

## 🚀 Hızlı Başlangıç

```bash
# 1. Icon ekle
cp logo.ico /app/frontend/build-resources/icon.ico
cp logo.png /app/frontend/build-resources/icon.png

# 2. GitHub'a yükle
cd /app
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/USER/whatgram.git
git push -u origin main

# 3. Actions'da izle
# GitHub.com > repo > Actions

# 4. Dosyaları indir
# Actions > Son run > Artifacts
```

---

## 🔗 Faydalı Linkler

- **GitHub Actions Dokümantasyon**: https://docs.github.com/en/actions
- **Electron Builder Dokümantasyon**: https://www.electron.build
- **Workflow Syntax**: https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions

---

🎉 **Otomatik build sisteminiz hazır!**

Her commit'te tüm platformlar için otomatik build alın! 🚀
