# 🌟 WhatGram - Unified Messaging Platform

**Tüm platformlarda çalışan birleşik mesajlaşma uygulaması**

WhatsApp, Telegram ve WhatGram ağlarını tek bir uygulamada birleştiren, AI destekli çoklu dil desteğine sahip modern mesajlaşma platformu.

---

## 🚀 HIZLI BUILD - TÜM PLATFORMLAR

### ⭐ GitHub Actions ile Otomatik Build (ÖNERİLEN)

**3 Adımda Tüm Platformlar:**

```bash
# 1. Icon dosyalarını hazırla
cp your-logo.ico /app/frontend/build-resources/icon.ico
cp your-logo.png /app/frontend/build-resources/icon.png

# 2. GitHub'a yükle
cd /app
git init
git add .
git commit -m "WhatGram - All platforms ready"
git remote add origin https://github.com/KULLANICI_ADINIZ/whatgram.git
git push -u origin main

# 3. GitHub Actions otomatik build yapar!
# 15-20 dakika sonra:
# ✅ Windows: WhatGram-Setup.exe, WhatGram-Portable.exe
# ✅ macOS: WhatGram.dmg
# ✅ Linux: WhatGram.AppImage, .deb, .rpm
```

**Dosyaları İndirme:**
1. GitHub repo > Actions > Son workflow
2. Artifacts bölümünden indir

**Detaylar:** [GITHUB_ACTIONS_BUILD.md](GITHUB_ACTIONS_BUILD.md)

---

## 📱 Desteklenen Platformlar

| Platform | Dosya | Durum | Build Rehberi |
|----------|-------|-------|---------------|
| **Windows** | Setup.exe / Portable.exe | ✅ Hazır | [WINDOWS_BUILD_GUIDE.md](WINDOWS_BUILD_GUIDE.md) |
| **macOS** | .dmg / .zip | ✅ Hazır | [GITHUB_ACTIONS_BUILD.md](GITHUB_ACTIONS_BUILD.md) |
| **Linux** | AppImage / .deb / .rpm | ✅ Hazır | [GITHUB_ACTIONS_BUILD.md](GITHUB_ACTIONS_BUILD.md) |
| **iOS** | .ipa | ✅ Hazır | [BUILD_GUIDE.md](BUILD_GUIDE.md) |
| **Android** | .apk / .aab | ✅ Hazır | [BUILD_GUIDE.md](BUILD_GUIDE.md) |

---

## ✨ Özellikler

- ✅ **Unified Inbox** - Tüm platformlardan mesajlar tek yerde
- ✅ **AI Çeviri** - OpenAI GPT-4o-mini ile 12 dil
- ✅ **Gerçek Zamanlı** - WebSocket mesajlaşma
- ✅ **Dosya Paylaşımı** - Görsel, video, dosya
- ✅ **Grup & Kanal** - Yönetim ve mesajlaşma
- ✅ **OTP Auth** - Güvenli telefon doğrulama
- ✅ **System Tray** - Arka planda çalışma (desktop)
- ✅ **Offline Mode** - İnternet olmadan çalışma

---

## 📦 Build Seçenekleri

### Option 1: GitHub Actions (Tüm Platformlar)
→ [GITHUB_ACTIONS_BUILD.md](GITHUB_ACTIONS_BUILD.md)

### Option 2: Windows .exe (Manuel)
→ [WINDOWS_EXE_QUICK_START.md](WINDOWS_EXE_QUICK_START.md)

### Option 3: iOS IPA (EAS Build)
→ [BUILD_GUIDE.md](BUILD_GUIDE.md)

---

## 📂 Proje Dosyaları

```
/app/
├── .github/workflows/       # CI/CD otomasyonu
├── backend/                 # FastAPI + MongoDB
├── frontend/                # React + Electron
├── mobile/                  # React Native + Expo
└── docs/                    # Tüm rehberler
```

---

## 🎯 Hızlı Komutlar

```bash
# Windows Desktop Build
cd /app/frontend && yarn electron-build

# iOS Mobile Build  
cd /app/mobile && eas build --platform ios

# Android Mobile Build
cd /app/mobile && eas build --platform android

# Geliştirme Modu
cd /app/frontend && yarn electron-dev
cd /app/mobile && yarn start
```

---

## 📚 Tüm Rehberler

1. **[GITHUB_ACTIONS_BUILD.md](GITHUB_ACTIONS_BUILD.md)** - Otomatik build (TÜM PLATFORMLAR)
2. **[WINDOWS_EXE_QUICK_START.md](WINDOWS_EXE_QUICK_START.md)** - Windows hızlı başlangıç
3. **[WINDOWS_BUILD_GUIDE.md](WINDOWS_BUILD_GUIDE.md)** - Windows detaylı rehber
4. **[BUILD_GUIDE.md](BUILD_GUIDE.md)** - iOS/Android build
5. **[mobile/README.md](mobile/README.md)** - React Native geliştirme

---

## 🎉 Sonuç

**WhatGram hazır!**

- ✅ Backend API: Çalışıyor ve test edildi
- ✅ Web App: React ile hazır
- ✅ Desktop Apps: Electron ile Windows/macOS/Linux
- ✅ Mobile Apps: React Native ile iOS/Android
- ✅ CI/CD: GitHub Actions otomatik build

**Tek yapmanız gereken:**
1. Icon dosyalarını eklemek
2. GitHub'a push etmek
3. Build'leri indirmek

🚀 **Başarılar!**
