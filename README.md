# ZooCard AR

Aplikasi Android Augmented Reality (AR) edukasi satwa yang berjalan 100% offline tanpa koneksi internet. Arahkan kamera belakang HP ke kartu marker QR ZooCard untuk memunculkan model 3D satwa animasi lengkap dengan suara satwa asli, narasi Bahasa Indonesia, fakta singkat, perbandingan tinggi nyata, foto ekspedisi, dan kuis.

## Daftar 5 Satwa & Kode Marker QR

| Kode QR | Nama Satwa | Nama Ilmiah | Status Konservasi | Habitat Asli |
| :--- | :--- | :--- | :--- | :--- |
| `ZC-01` | Harimau Sumatra | *Panthera tigris sumatrae* | Kritis (CR) | Hutan Hujan Sumatra, Indonesia |
| `ZC-02` | Komodo | *Varanus komodoensis* | Terancam (EN) | Pulau Komodo & Rinca, NTT |
| `ZC-03` | Gajah Sabana Afrika | *Loxodonta africana* | Terancam (EN) | Sabana Afrika |
| `ZC-04` | Jerapah | *Giraffa camelopardalis* | Rentan (VU) | Sabana Afrika |
| `ZC-05` | Penguin Kaisar | *Aptenodytes forsteri* | Hampir Terancam (NT) | Benua Es Antartika |

Catatan: kartu lama Penguin Kaisar berkode `ZC-06` tetap dikenali dan otomatis diarahkan ke `ZC-05`.

## Fitur Utama

- **100% Offline di Perangkat:** Seluruh model 3D (`.glb`), 5 klip suara satwa (`.wav`), Three.js r160, dan pemindai QR (`jsQR`) dibundel di dalam APK.
- **Mode Coba Tanpa Kartu:** Pengguna baru yang belum memegang kartu fisik tetap bisa mencoba model 3D Harimau Sumatra langsung dari layar kamera atau layar izin kamera.
- **Interaksi Langsung pada Model 3D:** Geser untuk memutar, cubit untuk memperbesar, ketuk hewan untuk suara dan animasi, tombol **Beri Makan** sesuai diet tiap satwa, tombol **Tinggi 1,2 m** untuk membandingkan ukuran satwa dengan tinggi anak, serta **Mode Fokus** untuk menyembunyikan panel.
- **Suara Satwa Asli & Narasi Bahasa Indonesia:** Memutar rekaman suara satwa lokal diikuti narasi fakta menggunakan Android native `TextToSpeech` (`id-ID`).
- **Kartu Foto Ekspedisi (Foto AR):** Menggabungkan tampilan kamera dan model 3D ke dalam bingkai kartu lapangan (720x960 PNG) lalu menyimpannya ke galeri (`Pictures/ZooCardAR`).
- **Info & Kuis 3 Soal per Satwa:** Profil fisik (kecepatan, ukuran, berat), penjelasan status konservasi IUCN, dan 3 soal pilihan ganda berpenjelasan untuk setiap satwa.
- **Paspor Penjelajah & Bandingkan 2 Satwa:** Mencatat progres kartu terpindai, fakta dibaca, dan stempel kuis di `localStorage`, dilengkapi tab perbandingan 2 satwa berdampingan serta profil nama penjelajah lokal opsional tanpa login.

## Struktur Proyek

```text
.
├── app/
│   ├── build.gradle.kts
│   └── src/main/
│       ├── AndroidManifest.xml
│       ├── java/com/zoocard/ar/MainActivity.kt
│       ├── res/
│       │   ├── drawable/
│       │   │   ├── ic_launcher.xml
│       │   │   └── launch_splash.xml
│       │   └── values/
│       │       ├── strings.xml
│       │       └── styles.xml
│       └── assets/www/
│           ├── mobile-ar.html
│           ├── models/          # 5 model 3D satwa (.glb)
│           ├── sounds/          # 5 suara satwa (.wav)
│           └── vendor/          # Three.js r160 & jsQR lokal
├── build.gradle.kts
├── gradle.properties
└── settings.gradle.kts
```

## Cara Build APK

### Prasyarat
- JDK 17 atau JDK 21 (direkomendasikan JDK 21 untuk Gradle 8.9)
- Android SDK (API 34, `minSdk 24`, `targetSdk 34`)
- Gradle 8.9 (atau buka proyek langsung di Android Studio)

### Langkah Build
1. Buat file `local.properties` di root proyek dan arahkan ke lokasi Android SDK Anda:
   ```properties
   sdk.dir=C:\\Users\\<NamaUser>\\AppData\\Local\\Android\\Sdk
   ```
2. Jalankan build debug:
   ```bash
   gradle assembleDebug
   ```
3. File APK hasil build tersedia di:
   ```text
   app/build/outputs/apk/debug/app-debug.apk
   ```

## Atribusi Aset

### Model 3D (Sketchfab CC BY / CC BY-NC)
- Tiger by Blender Artist (`@moizmuhammad373`)
- Model 116A Komodo Dragon by DigitalLife3D (NHM Vienna)
- Elephant Animation Idle by GremorySaiyan
- Giraffe by Amx360
- Emperor Penguin Looking Around by yinjo

### Suara Satwa (Wikimedia Commons)
- Harimau: `439280 schots angry-tiger.wav` oleh schots (CC0)
- Desisan Komodo: diadaptasi dari `Cat hissing` oleh Zabuhailo (CC0)
- Gajah: `Elephant voice - trumpeting.ogg` oleh தகவலுழவன் (CC0)
- Jerapah: `Giraffe grunt.oga` oleh Anton Baotic, Florian Sicks, dan Angela S. Stoeger (CC BY-SA 4.0)
- Penguin: `King Penguin Rookery Audio.oga` oleh Hullwarren (CC BY-SA 3.0)
