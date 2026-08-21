# 📅 Setup Kalender Jawa di Google Calendar

**Untuk Kak Du - Blitar**

---

## 🎯 Opsi yang Tersedia

### Opsi 1: Subscribe Kalender (PALING MUDAH) ⭐
### Opsi 2: Embed Calendar di Website
### Opsi 3: Export iCal ke Device

---

## 📌 OPSI 1: SUBSCRIBE KALENDER KE GOOGLE CALENDAR

### Step 1: Generate File ICS

Jalankan di folder project:
```bash
node generate-ics.js
```

Hasil: File `kalender-jawa.ics` (total ~365 events untuk 1 tahun)

### Step 2: Upload ke GitHub

Push file ke GitHub repo Kak Du:
```bash
git add kalender-jawa.ics
git commit -m "Add Kalender Jawa ICS file"
git push
```

### Step 3: Dapatkan Raw URL

Di GitHub:
1. Buka file: `kalender-jawa.ics`
2. Klik tombol "Raw"
3. Copy URL (format: https://raw.githubusercontent.com/kakdu/kalender-jawa/main/kalender-jawa.ics)

### Step 4: Subscribe ke Google Calendar

Buka Google Calendar (https://calendar.google.com)

**Opsi A: Desktop**
```
1. Di sidebar kiri → "+ Kalender lain" (di sebelah Other calendars)
2. Klik "Subscribe to calendar"
3. Paste raw URL dari GitHub
4. Klik "Subscribe"
5. ✅ Selesai! Kalender Jawa muncul
```

**Opsi B: Mobile**
```
1. Buka Google Calendar app
2. Settings → Add calendar → Subscribe to calendar
3. Paste URL
4. Subscribe
5. ✅ Selesai!
```

### Step 5: Customize (Opsional)

Di Google Calendar:
- Klik "..." di Kalender Jawa
- "Settings"
  - Ubah warna
  - Hide/show berdasarkan neton
  - Set notification

---

## 📊 OPSI 2: EMBED CALENDAR DI WEBSITE

Kalau Kak Du mau tampilkan di blog/website pribadi:

### Setup:

1. Generate ICS:
```bash
node generate-ics.js
```

2. Create HTML embed:
```html
<iframe src="https://calendar.google.com/calendar/embed?src=[CALENDAR_ID]@group.calendar.google.com" 
  style="border: 0" width="800" height="600" frameborder="0" scrolling="no"></iframe>
```

3. Atau gunakan Google Calendar Gadget:
```html
<script src="https://www.gstatic.com/calendar/api/calendar_v3/js/client.js"></script>
<script>
  gapi.load('client', function() {
    gapi.client.calendar.events.list({
      'calendarId': 'primary',
      'maxResults': 10,
      'orderBy': 'startTime',
      'singleEvents': true,
      'timeMin': new Date().toISOString()
    }).then(function(response) {
      // Display events
    });
  });
</script>
```

---

## 💾 OPSI 3: EXPORT KE ICAL DEVICE

### Untuk Sync Offline:

1. Generate ICS:
```bash
node generate-ics.js
```

2. Download `kalender-jawa.ics`

3. Import ke:
   - **Apple Calendar**: Double-click file
   - **Outlook**: File → Open & Export → Import
   - **Android**: Buka file dengan calendar app
   - **iOS**: Share → Add to Calendar

---

## 🔄 AUTO-UPDATE (Optional)

Kalau mau calendar selalu update otomatis:

### Setup GitHub Actions untuk auto-generate ICS

Buat file: `.github/workflows/generate-ics.yml`

```yaml
name: Generate ICS Calendar

on:
  schedule:
    # Run setiap hari jam 12:00 WIB (05:00 UTC)
    - cron: '0 5 * * *'
  workflow_dispatch:

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      
      - uses: actions/setup-node@v2
        with:
          node-version: '16'
      
      - name: Generate ICS
        run: node generate-ics.js
      
      - name: Commit & Push
        run: |
          git config user.name "GitHub Actions"
          git config user.email "actions@github.com"
          git add kalender-jawa.ics
          git commit -m "Auto-generate ICS calendar" || true
          git push
```

Hasil: File `.ics` auto-update setiap hari!

---

## 🎨 WARNA NETON DI CALENDAR

Google Calendar akan menampilkan dengan warna:

```
Neton 2 (Jodoh/Bagus)    → 🟢 Hijau
Neton 6 (Lancar/Bagus)   → 🟢 Hijau

Neton 3 (Selamat/Sedang) → 🟠 Orange
Neton 5 (Prihatin/Sedang)→ 🟠 Orange

Neton 1 (Mati/Jelek)     → 🔴 Merah
Neton 4 (Cerai/Jelek)    → 🔴 Merah
Neton 7 (Pegat/Jelek)    → 🔴 Merah
```

---

## 📱 SHARE KALENDER

Setelah di-subscribe, Kak Du bisa share ke orang lain:

### Di Google Calendar:
1. Klik "..." di Kalender Jawa
2. "Settings and sharing"
3. Scroll ke "Share with specific people"
4. Add email/link
5. Send

### Atau share URL raw:
```
https://raw.githubusercontent.com/kakdu/kalender-jawa/main/kalender-jawa.ics
```

---

## 🔍 TROUBLESHOOTING

### Calendar tidak muncul?
- ✅ Cek URL raw sudah benar
- ✅ File .ics valid (buka di text editor)
- ✅ Tunggu 24 jam untuk refresh pertama

### Events tidak update?
- ✅ Set refresh interval di calendar settings
- ✅ Manual refresh: klik "Refresh" di calendar
- ✅ Regenerate .ics: `node generate-ics.js` + git push

### Terlalu banyak events?
- Edit `generate-ics.js` line ~80: ubah periode dari 365 ke jumlah hari yg diinginkan
- Contoh: hanya 3 bulan = ubah `endDate` ke `+3 bulan`

---

## 📋 CHECKLIST SETUP

- [ ] Run: `node generate-ics.js`
- [ ] File `kalender-jawa.ics` terbuat
- [ ] Push ke GitHub
- [ ] Dapatkan raw URL
- [ ] Subscribe di Google Calendar
- [ ] Verify: Event muncul dengan warna neton
- [ ] (Opsional) Setup GitHub Actions auto-generate
- [ ] (Opsional) Share ke orang lain

---

## 🎯 NEXT STEPS

Setelah berhasil setup:

1. **Personalize** warna & notifikasi di Google Calendar
2. **Share** link ke teman/keluarga yang ingin lihat hari baik
3. **Monitor** neton untuk planning event penting
4. **Feedback** kalau ada yang perlu diubah

---

## 📞 SUPPORT

Kalau ada masalah:
- Chat langsung dengan detail error
- Share screenshot error message
- Cek apakah file .ics valid

---

**Dibuat untuk Kak Du - August 18, 2026**
Referensi: Blog arrjawa.blogspot.com
