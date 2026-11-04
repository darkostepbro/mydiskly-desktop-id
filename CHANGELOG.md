# Catatan Perubahan (Changelog) - MyDiskly 💽

Seluruh pembaruan dan perubahan penting pada aplikasi **MyDiskly** akan didokumentasikan di dalam file ini.

---

## [1.1.2026] - 2026-11-04
### 🚀 MyDiskly v1.1.2026 - Porting ke RUST!

#### 🌟 Terobosan Arsitektur Utama
- **100% Mesin Native Rust**: Migrasi total dari basis lama Python / PyInstaller ke bahasa pemrograman Rust murni (`eframe` / `egui 0.29` dengan render native Win32 Glow).
- **Nol Dependensi Eksternal**: Menghilangkan dependensi Python runtime, DLL wrapper ctypes, Chromium, maupun komponen WebView2.
- **Konsumsi Memori Ultra-Rendah**:
  - Pengurangan penggunaan RAM aktif hingga **80%** (~30–40 MB working set).
  - Pengurangan penggunaan RAM saat diminimalkan ke System Tray hingga **~3–5 MB** berkat optimasi Win32 `SetProcessWorkingSetSize`.
- **Waktu Cold Startup Instan**: Akselerasi peluncuran aplikasi dari ~3.5 detik terpangkas drastis menjadi **< 50 milidetik**.

#### ✨ Fitur & Peningkatan Baru
- **Docking Sisi Kanan (Right-Docked)**: Mode Always-On-Top vertikal 420 px yang menempel presisi di batas kerja Windows (`SPI_GETWORKAREA`) dengan efek native Windows Acrylic Dark Blur (`SetWindowCompositionAttribute` + `DwmSetWindowAttribute`).
- **Penjelajah Partisi Interaktif**: Klik kartu partisi untuk membuka Windows Explorer atau menampilkan dialog properti drive secara langsung.
- **Diagnostik Drive Fisik S.M.A.R.T**: Pendeteksian tipe penyimpanan fisik (NVMe, SSD, HDD) lengkap dengan persentase kesehatan (**Bold %**) dan sensor suhu (**Bold °C**).
- **Grafik Gelombang I/O Real-Time 30 Detik**: Kanvas grafik sub-pixel 60 FPS untuk pemantauan throughput baca/tulis di bagian bawah Dashboard.
- **Smart Cleaner Aman dengan Isolasi Cache Browser**:
  - Pemindai khusus untuk cache Google Chrome, Brave, dan Microsoft Edge.
  - Jaminan 100% aman: tidak menyentuh riwayat penjelajahan, cookies, bookmark, atau sesi login.
  - Perlindungan cache sistem dengan label status `[User mode]` / `[Admin mode]` dan tombol elevasi hak akses satu klik.
  - Dialog modal konfirmasi penyelesaian dengan efek *softblur*.
- **Spesifikasi Perangkat Keras & Notifikasi Audio**:
  - Tabel audit 15 spesifikasi hardware tanpa *scroll* horizontal.
  - Peringatan batas kapasitas cache (`500MB`, `800MB`, `1GB`, `2GB`, `Kustom`, `Tidak Pernah`) dengan notifikasi Windows Toast dan efek suara `interface.wav`.
- **Komponen Persistensi Mandiri**:
  - `mydiskly.ini`: Konfigurasi preferensi aplikasi.
  - `myspecs.ini`: Berisi header `[{user} - {computer}]` dan data spesifikasi lengkap yang diperbarui otomatis saat pergantian perangkat atau deteksi USB.
  - `historydiskhealth.ini`: Log riwayat tanggal pengecekan kesehatan partisi.
- **Setup Wizard & Uninstaller Mandiri (`480 × 300` px)**:
  - Roadmap instalasi 3 langkah (`Welcome` ➔ `Installing` ➔ `Complete`) dengan tombol toggle rounded modern.
  - Eksekusi senyap di latar belakang tanpa jendela CMD (`CREATE_NO_WINDOW` & Win32 `ShellExecuteW`).
  - File instalasi bersih: hanya 6 file di folder `%LOCALAPPDATA%\Programs\MyDiskly`.
  - 4 lapis terminasi paksa untuk memastikan pencopotan pemasangan bersih tanpa sisa.

---

## [1.0.2026] - 2026-10-28
### Rilis Perdana (Prototipe Python)
- Prototipe awal berbasis Python 3.11, CustomTkinter, dan `disktrex.dll`.
