# 📱 Kalender Jawa - Pasaran, Wuku, Neptu & Neton

**Aplikasi Kalender Jawa untuk Android & Web**

## 📚 Deskripsi

Aplikasi interaktif untuk menampilkan:
- **Pasaran** (Legi, Pahing, Pon, Wage, Kliwon)
- **Wuku** (30 siklus tahunan)
- **Neptu** (nilai gabungan hari + pasaran)
- **Neton** (hasil interpretasi: baik/sedang/jelek)

Dengan kalkulator detail, kalender bulanan interaktif, dan siap sinkron Google Calendar.

## 🎯 Fitur

✅ **Kalender Jawa Interactive**
- Month view dengan warna neton
- Detail weton, wuku, neptu setiap tanggal
- Navigasi prev/next bulan

✅ **Kalkulator Neton**
- Input tanggal → result neptu + neton
- Breakdown perhitungan (hari neptu + pasaran neptu)
- Meaning & arti neton

✅ **Responsive Design**
- Mobile friendly (Android 6+)
- Web browser compatible
- Offline-ready

✅ **Siap Production**
- Build ke APK native
- Deploy ke web (vercel, github pages, dll)
- Performance optimized

## 🚀 Quick Start

### Opsi 1: HTML Browser (Instant)
```bash
# Buka: kalender-jawa.html di browser
# Langsung jalan, tidak perlu install
```

### Opsi 2: Build APK (15 min)
```bash
npm install
npm run cap:sync
npm run cap:open android
# Build di Android Studio
```

### Opsi 3: Deploy Web (5 min)
```bash
npm run build
vercel deploy
```

## 📖 Dokumentasi

- **INSTALASI.md** - Setup lengkap & build guide
- **SETUP_GUIDE.md** - Alternatif guide & troubleshooting
- **src/App.jsx** - React component utama
- **kalender-jawa.html** - Standalone HTML version

## 🧮 Kalkulasi Jawa

### Neptu Hari (7-hari):
```
Ahad=5, Senen=4, Selasa=3, Rabu=7, Kamis=8, Jumat=6, Sabtu=9
```

### Neptu Pasaran (5-hari):
```
Legi=5, Pahing=9, Pon=7, Wage=4, Kliwon=8
```

### Neton (Hasil Neptu mod 7):
```
1=Mati (jelek) | 2=Jodoh (bagus) | 3=Selamat (sedang)
4=Cerai (jelek) | 5=Prihatin (sedang) | 6=Lancar (bagus) | 7=Pegat (jelek)
```

## 🔧 Tech Stack

- **Frontend:** React 18 + Vite
- **Styling:** Tailwind CSS
- **Mobile:** Capacitor (Android/iOS native)
- **Build:** NPM + Vite + Gradle (Android)

## 📱 Platform Support

| Platform | Status | Notes |
|----------|--------|-------|
| Android | ✅ | v6.0+ (API 23+) |
| iOS | ⏳ | Planned v1.1 |
| Web | ✅ | All modern browsers |
| PWA | ✅ | Installable |

## 🎨 Features Roadmap

### v1.0 (Current)
- ✅ Kalender Jawa interactive
- ✅ Neton calculator
- ✅ Responsive design
- ✅ HTML + React versions

### v1.1 (Coming Soon)
- 🔜 Google Calendar integration
- 🔜 Push notifications
- 🔜 Event recommendation by neton
- 🔜 Dark mode

### v2.0 (Future)
- 🔜 Primbon extended features
- 🔜 Historical calendar data
- 🔜 Export calendar
- 🔜 Offline sync

## 🧪 Testing

```bash
# Dev mode
npm run dev

# Build
npm run build

# Preview production build
npm run preview

# Capacitor
npm run cap:sync
npm run cap:open android
```

## 📞 Support

Untuk Kak Du:
- Update kalkulasi? → Edit `src/App.jsx` NETON_HASIL
- Bug report? → Chat langsung
- Fitur baru? → Requirement discussion

## 📜 Credits

- **Kalender Data:** Primbon Jawa (arrjawa.blogspot.com)
- **Dev:** Claude (Anthropic)
- **Client:** Kak Du (Blitar, East Java)

## 📄 License

Educational & Non-commercial use

---

**Status:** ✅ v1.0.0 Production Ready  
**Last Update:** August 18, 2026  
**Platform:** Android 6+ | Web Browser | PWA
