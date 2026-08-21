# 📱 KALENDER JAWA - PANDUAN INSTALASI & BUILD

**Dibuat untuk: Kak Du (Blitar, East Java)**  
**Status:** v1.0.0 - SIAP PRODUKSI  
**Tanggal:** August 18, 2026

---

## 🚀 QUICK START (Paling Cepat)

### Opsi 1: Buka HTML di Browser (0 menit setup)
```
1. Ambil file: kalender-jawa.html
2. Pindah ke device Android via USB/cloud
3. Buka File Manager → cari file
4. Tap → Buka dengan Browser
✅ Langsung bisa pakai!
```

### Opsi 2: Build APK Native (15-30 menit setup)
```bash
# Persiapan
- Install Node.js
- Install Android Studio + SDK
- Clone/download project ini

# Build
npm install
npm run cap:sync
npm run cap:open android

# Hasil: APK file siap install di phone
```

---

## 📋 PERSYARATAN SISTEM

### Untuk Web/HTML (Minimal):
- ✓ Browser modern (Chrome, Firefox, Safari)
- ✓ RAM: 512MB+
- ✓ Koneksi internet (pertama kali) / Offline (setelah load)

### Untuk Build APK (Standar Development):
- **OS:** Windows, macOS, or Linux
- **Node.js:** v16+ (https://nodejs.org)
- **Java:** JDK 11+ 
- **Android SDK:** API 28+ (via Android Studio)
- **RAM:** 4GB+ recommended
- **Disk:** 5GB+ (untuk Android SDK + NDK)

---

## 🔧 INSTALASI STEP-BY-STEP

### Step 1: Install Dependencies

#### Linux/macOS:
```bash
# Install Node.js (jika belum ada)
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

# Clone/extract project
unzip kalender-jawa.zip
cd kalender-jawa

# Install npm dependencies
npm install
```

#### Windows:
```bash
# Download & install Node.js dari https://nodejs.org
# Buka Command Prompt / PowerShell

# Navigate ke project folder
cd C:\Users\[username]\kalender-jawa

# Install dependencies
npm install
```

### Step 2: Build Web Assets
```bash
# Build optimized web version
npm run build

# Hasil: folder 'dist' yang siap deploy
```

### Step 3: Setup Capacitor (Untuk APK)

```bash
# Tambahkan platform Android
npm run cap:add:android

# Sync dengan native code
npm run cap:sync

# Buka di Android Studio
npm run cap:open android
```

### Step 4: Build APK di Android Studio

1. **Tunggu gradle build selesai** (pertama kali ~2-3 menit)

2. **Build unsigned APK (testing):**
   ```
   Menu: Build → Build Bundle(s) / APK(s) → Build APK(s)
   Hasil: android/app/debug/app-debug.apk
   ```

3. **Build signed APK (production):**
   ```
   Menu: Build → Generate Signed Bundle / APK
   - Format: APK
   - Create new keystore atau gunakan yang ada
   - Pilih: debug key (untuk testing) atau buat production key
   - Finish
   
   Hasil: android/app/release/app-release.apk
   ```

4. **Install ke device:**
   ```bash
   # Plug USB device atau start emulator
   
   # Di Android Studio:
   Run → Run 'app' (atau tekan Shift+F10)
   
   # Atau via command line:
   adb install android/app/debug/app-debug.apk
   ```

---

## 🌐 DEPLOY KE WEB (Opsional)

### Vercel (Recommended - FREE):
```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
vercel

# Follow prompts, selesai!
# URL: https://kalender-jawa.vercel.app
```

### GitHub Pages:
```bash
# Build
npm run build

# Push ke GitHub
git add .
git commit -m "Deploy Kalender Jawa v1.0"
git push origin main

# Settings → Pages → Deploy from main/dist branch
```

### Self-hosted (VPS/Dedicated Server):
```bash
# Build
npm run build

# Copy dist/ folder ke server
scp -r dist/ user@server.com:/var/www/kalender-jawa/

# Setup nginx/apache untuk serve static files
# Result: http://your-domain.com/
```

---

## 📦 FILE STRUCTURE

```
kalender-jawa/
├── src/
│   ├── App.jsx              # Main React component
│   ├── main.jsx             # Entry point
│   └── index.css            # Tailwind styles
├── android/                 # Android native (auto-generated)
├── dist/                    # Build output (auto-generated)
│
├── package.json             # Dependencies
├── vite.config.js           # Vite build config
├── tailwind.config.js       # Tailwind config
├── capacitor.config.json    # Capacitor config
├── index.html               # HTML template
│
├── kalender-jawa.html       # Standalone HTML version
├── INSTALASI.md             # File ini
├── SETUP_GUIDE.md           # Alternative guide
└── README.md                # Project info
```

---

## 🧪 TESTING CHECKLIST

Sebelum release ke production:

- [ ] **Kalender View:**
  - [ ] Navigate bulan sebelum/sesudah
  - [ ] Tanggal hari ini highlighted
  - [ ] Pasaran muncul benar (Legi, Pahing, Pon, dll)
  - [ ] Wuku terlihat di setiap tanggal
  - [ ] Neton color benar (hijau=bagus, orange=sedang, merah=jelek)

- [ ] **Kalkulator:**
  - [ ] Input tanggal → display weton, wuku, neptu, neton
  - [ ] Neptu = hari neptu + pasaran neptu
  - [ ] Neton = (neptu mod 7), hasil 1-7
  - [ ] Tabel perhitungan muncul
  - [ ] Meaning/arti neton sesuai

- [ ] **Performance:**
  - [ ] Load < 3 detik di 3G
  - [ ] Smooth scroll di 2000+ events
  - [ ] No lag saat navigate bulan

- [ ] **Device:**
  - [ ] Responsive di mobile (320px - 480px)
  - [ ] Responsive di tablet (768px - 1024px)
  - [ ] Responsive di desktop (1920px+)
  - [ ] Touch friendly (button size >= 44px)

- [ ] **Offline:**
  - [ ] Buka tanpa internet → semua feature work
  - [ ] Cache berfungsi
  - [ ] No console errors

---

## 🔄 UPDATE & MAINTENANCE

### Update Code:
```bash
# Kak Du koreksi perhitungan (misal neton values)
# Edit file: src/App.jsx → NETON_HASIL object

# Rebuild:
npm run build

# Redeploy:
npm run cap:sync
# Rebuild APK di Android Studio
```

### Update Dependencies:
```bash
npm update

# Atau check untuk updates:
npm outdated
```

### Version Bump:
```bash
# Edit package.json: "version": "1.0.1"
npm publish (jika di npm registry)
```

---

## 🐛 TROUBLESHOOTING

### Problem: "npm: command not found"
```
Solusi: Install Node.js dari https://nodejs.org
```

### Problem: "Cannot find Android SDK"
```
Solusi: 
1. Install Android Studio
2. Open → Tools → SDK Manager
3. Install "Android SDK Platform 28+"
4. Set ANDROID_HOME environment variable
```

### Problem: "APK build failed"
```
Solusi:
1. npm run cap:sync (ulang sync)
2. Di Android Studio: Build → Clean Project
3. Build → Rebuild Project
4. Try again
```

### Problem: "App crash at startup"
```
Check:
1. adb logcat (lihat error message)
2. Ensure Capacitor plugins loaded
3. Check capacitor.config.json
```

---

## 📞 KONTAK & SUPPORT

**Untuk Kak Du:**
- Update kalkulasi jawa? → Edit NETON_HASIL di src/App.jsx
- Add fitur baru? → Chat langsung koreksi/requirement
- Deploy masalah? → Debug via console + adb logcat

---

## 📜 LICENSE & CREDITS

- **Kalender Data:** Primbon Jawa (arrjawa.blogspot.com)
- **Tech Stack:** React 18 + Vite + Tailwind CSS + Capacitor
- **Built with:** ❤️ untuk komunitas Jawa

---

## 📝 CHANGELOG

### v1.0.0 (Aug 18, 2026)
- ✅ Kalender Jawa interactive dengan pasaran, wuku, neptu, neton
- ✅ Kalkulator detail dengan breakdown neptu
- ✅ Responsive design (mobile + web)
- ✅ HTML + React versions
- ✅ Capacitor APK build setup
- ⏳ Google Calendar integration (planned v1.1)
- ⏳ Push notifications (planned v1.1)

---

**Dibuat untuk: Kak Du, Electronics Technician, Blitar 🇮🇩**

Terakhir update: August 18, 2026
