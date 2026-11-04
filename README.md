# MyDiskly (Pure Native Rust Edition) 💽
> **Aplikasi Diagnostik Penyimpanan, Telemetri S.M.A.R.T, dan Pembersih Sistem Windows 11 & 10 Ultra-Ringan & Modern**

<p align="center">
  <img src="assets/icon.png" width="128" height="128" alt="MyDiskly Native Icon" />
</p>

<p align="center">
  <a href="https://github.com/darkostepbro/mydiskly-desktop-id/releases"><img src="https://img.shields.io/badge/Rilis-v1.1.2026-0B65E6?style=for-the-badge&logo=windows11&logoColor=white" alt="Rilis v1.1.2026" /></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/Lisensi-GPL--3.0-green?style=for-the-badge" alt="Lisensi GPL-3.0" /></a>
  <a href="https://www.rust-lang.org/"><img src="https://img.shields.io/badge/Bahasa-Rust%202021-DEA584?style=for-the-badge&logo=rust&logoColor=white" alt="Rust 2021" /></a>
  <a href="https://github.com/darkostepbro/mydiskly-desktop-id"><img src="https://img.shields.io/badge/Platform-Windows%2010%20%7C%2011%20(x64)-blue?style=for-the-badge&logo=windows" alt="Platform" /></a>
  <a href="https://github.com/darkostepbro/mydiskly-desktop-id/issues"><img src="https://img.shields.io/badge/Umpan%20Balik-Terbuka-orange?style=for-the-badge&logo=github" alt="Feedback" /></a>
</p>

---

## 📖 Tentang MyDiskly
**MyDiskly** adalah utilitas desktop berkinerja tinggi untuk diagnostik penyimpanan (*storage telemetry*), pemantauan kesehatan drive (S.M.A.R.T), audit spesifikasi perangkat keras, dan pembersih sampah sistem (*smart disk cleaner*) yang dibangun **100% murni menggunakan bahasa pemrograman Rust** (`eframe` / `egui 0.29` + native Glow Win32 rendering).

MyDiskly dirancang khusus untuk pengguna Windows 10 & Windows 11 (termasuk edisi modifikasi / *debloated* seperti *Ghost Spectre*, *AtlasOS*, *Tiny11*, maupun *ReviOS*) yang menginginkan aplikasi utilitas dengan **konsumsi memori ultra-rendah**, waktu startup instan, tampilan *docking* vertikal modern (*fluent dark blur UI*), tanpa dependensi Python, tanpa runtime WebView2 / Chromium, dan tanpa overhead JavaScript.

> **Publisher**: [Seroja Labs](https://serojalabs.sbs/mydiskly)  
> **Author**: [Darkostepbro](https://github.com/darkostepbro)  
> **Versi**: `1.1.2026`  
> **Kategori**: Native Installer & Portable Storage Suite  
> **Lisensi**: GNU General Public License v3.0 (GPL-3.0)  

---

## 🚀 Perbandingan Performa: Versi Lama (Python) vs Versi Baru (Pure Native Rust)

| Parameter / Metrik | Versi Lama (Python / PyInstaller) | Versi Baru (Pure Native Rust) | Peningkatan Kinerja |
| :--- | :--- | :--- | :--- |
| **Bahasa Pemrograman & Mesin** | Python 3.11 + Tkinter / ctypes | **100% Rust 2021 (Win32 + Glow)** | Nol Dependensi Runtime |
| **Penggunaan RAM (Aktif)** | ~110 MB – 180 MB | **~30 MB – 40 MB** | **Hemat Memori hingga 80%** |
| **Penggunaan RAM (Tray / Idle)**| ~75 MB – 90 MB | **~3 MB – 5 MB** | **Hemat Memori hingga 95%** |
| **Waktu Cold Startup** | 2.5 – 4.0 detik (Ekstraksi zip) | **< 50 milidetik (Instan)** | **50x Lebih Cepat** |
| **Dependensi Eksternal** | Python DLLs, MSVCRT, WebView2 | **Nol (Executable Mandiri)** | 100% Standalone |
| **Ukuran Paket Rilis (Zip)** | ~21 MB | **~2.29 MB** | **Ukuran 90% Lebih Ringkas** |
| **Kompatibilitas Windows** | Sering crash di Windows Lite | **Windows 10 & 11 x64 (Semua Edisi)** | Sangat Stabil & Tangguh |

---

## ✨ Fitur-Fitur Unggulan

### 1. 🖥️ Vertical Right-Docking & Native Acrylic Dark Blur
- Menempel vertikal secara presisi di sisi kanan layar desktop (`SPI_GETWORKAREA`) dengan lebar tetap **420 px**.
- Kemampuan **Always-On-Top** dengan tombol kendali jendela minimalis: **Close `[x]`** dan **Minimize `[—]`**.
- Efek visual *Dark Blur / Acrylic* asli Windows menggunakan `SetWindowCompositionAttribute` dan `DwmSetWindowAttribute` (`DWMWCP_ROUND`).
- Tombol sakelar dwibahasa instan saat aplikasi berjalan **`[ID | EN]`**, serta indikator izin hak akses: **`[User mode]`** (transparan/redup) dan **`[Admin mode]`** (terang).

### 2. 💽 Partisi Interaktif & Telemetri Real-Time
- **Kartu Partisi Interaktif**: Bar kapasitas penyimpanan visual dengan batas warna ergonomis (Normal / Warning / Critical). Klik pada kartu partisi untuk membuka menu tindakan cepat:
  - `1. Open file`: Membuka drive partisi langsung di Windows File Explorer.
  - `2. Properties`: Membuka dialog native *Drive Properties* Windows.
- **Diagnostik Drive S.M.A.R.T**: Pendeteksian fisik drive penyimpanan (NVMe, SSD, HDD), **Persentase Kesehatan (Bold %)**, **Suhu Sensor (Bold °C)**, dan total durasi aktif (*Power-On Hours*).
- **Grafik Gelombang I/O 30 Detik**: Kanvas grafik sub-pixel 60 FPS untuk akselerasi kecepatan baca (*Read*) dan tulis (*Write*) secara real-time yang tertambat di bagian bawah Dashboard.

### 3. 🧹 Smart Cleaner Aman dengan Isolasi Cache Browser
- **Pemindai Cache Browser Terisolasi**: Mendeteksi otomatis profil browser Google Chrome, Brave Browser, dan Microsoft Edge yang terpasang di komputer.
- **Jaminan 100% Aman**: Hanya membersihkan file cache (*System Cache, Code Cache, GPUCache, Service Worker Cache*). **Tidak akan pernah** menghapus riwayat penjelajahan (*history*), bookmark, cookies, maupun sesi login yang tersimpan.
- **Perisai Hak Akses Administratif**: Item cache sistem yang membutuhkan izin administrator otomatis berstatus *read-only* saat berada di Mode User, dilengkapi tombol elevasi instan (*Run as Administrator*).
- **Dialog Modal Penyelesaian**: Animasi progress bar yang halus dan dialog popup modern dengan latar belakang *softblur* yang menampilkan total memori yang berhasil dibebaskan.

### 4. ⚙️ Spesifikasi Perangkat Keras & Notifikasi Audio
- **Tabel Spesifikasi Terstruktur**: Menyajikan 15 parameter teknis perangkat keras (OS Build, CPU, GPU, RAM, Motherboard, BIOS Mode, Storage, Audio, Network, Peripherals) secara rapi dan presisi tinggi tanpa scroll horizontal.
- **Pengingat Batas Cache Proaktif**: Pilihan ambang batas peringatan kapasitas cache (`500MB`, `800MB`, `1GB`, `2GB`, `Kustom MB/GB`, `Tidak Pernah`).
- **Efek Suara Antarmuka Asli**: Memutar nada audio khas (`interface.wav`) saat pembersihan selesai atau ketika ambang batas peringatan tercapai.
- **Dukungan Windows Focus Assist**: Mendeteksi setelan notifikasi dan mode hening Windows Toast secara otomatis.

### 5. 📁 Sinkronisasi Komponen Persistensi Mandiri
MyDiskly secara otomatis mengelola dan memperbarui 3 file konfigurasi:
- **`mydiskly.ini`**: Menyimpan preferensi pengguna (tema, bahasa, startup registry, dan batas notifikasi).
- **`myspecs.ini`**: Berisi header perangkat `[{user} - {computer}]` dan 15 baris audit perangkat keras lengkap. Otomatis terbarui jika terjadi penggantian komponen atau pemasangan drive USB (*hotplug*).
- **`historydiskhealth.ini`**: Log riwayat tanggal pengecekan kesehatan partisi (`[02/nov/2026]`, dll.) yang tersimpan secara terstruktur.

### 6. 📦 Setup Wizard 3 Halaman & Uninstaller Suite Mandiri (`480 × 300` px)
- Biner instalasi mandiri (**`MyDiskly-Setup.exe`**) dan pencopot pemasangan (**`Uninstall.exe`**).
- **Roadmap 3 Tahapan**: `1. Welcome` ➔ `2. Installing` ➔ `3. Complete` dengan indikator kapsul dan sakelar *toggle* full rounded.
- **Sakelar Pengaturan Cepat**: `Create the shortcut`, `Run as Administrator`, `Pin on Start Menu`, `Open File Location`.
- **Eksekusi Latar Belakang Senyap**: 100% bebas dari kedipan jendela CMD melalui Win32 `CREATE_NO_WINDOW` dan `ShellExecuteW`.
- **Instalasi Bersih (Zero Clutter)**: Hanya menyebarkan 6 file resmi di `%LOCALAPPDATA%\Programs\MyDiskly`:
  1. `MyDiskly.exe`
  2. `Uninstall.exe`
  3. `mydiskly.ini`
  4. `myspecs.ini`
  5. `historydiskhealth.ini`
  6. `LICENSE.txt`
- **Pencopotan Pemasangan Permanen**: Menghentikan paksa aplikasi MyDiskly yang sedang berjalan di latar belakang atau tray melalui 4 lapis terminasi, membuka kunci folder, dan menghapus seluruh file serta entri registry tanpa meninggalkan sisa sampah.

---

## 🏛️ Struktur Workspace Cargo

```
mydiskly-desktop-id/
├── .gitignore                         # Filter file target/, *.ini, *.log, *.signal
├── Cargo.lock                         # Manifest ketergantungan terkunci
├── Cargo.toml                         # Workspace root dengan konfigurasi LTO & optimasi
├── CHANGELOG.md                       # Catatan rilis v1.1.2026
├── LICENSE                            # GNU General Public License v3.0 (GPL-3.0)
├── README.md                          # Dokumentasi utama Bahasa Indonesia
├── build.bat                          # Skrip build otomasi 1-klik (Command Prompt / CMD)
├── build.ps1                          # Skrip build otomasi 1-klik (PowerShell)
├── crates/
│   └── mydiskly-core/                 # Shared Win32 Kernel, Telemetri & Engine Library
│       ├── Cargo.toml
│       └── src/
│           ├── lib.rs                 # Ekspor modul library
│           ├── gatekeeper.rs          # Verifikasi sistem operasi Windows 10 & 11
│           ├── disk_telemetry.rs      # Statistik partisi & buffer grafik I/O 30 detik
│           ├── smart_diagnostics.rs   # Sensor S.M.A.R.T drive fisik (NVMe, SSD, HDD)
│           ├── hotplug_monitor.rs     # Deteksi hotplug USB real-time
│           ├── hardware_specs.rs      # Mesin audit 15 spesifikasi perangkat keras
│           ├── cleaner_engine.rs      # Mesin pembersih cache & isolasi browser
│           ├── ini_manager.rs         # Manajemen file .ini (Config, Specs, History)
│           └── models/                # Struct telemetri, konfigurasi, dan pembersih
├── apps/
│   ├── mydiskly-app/                  # Aplikasi Utama Desktop (Right-Docked Fluent UI)
│   │   ├── Cargo.toml                 # Target biner: MyDiskly.exe
│   │   ├── build.rs                   # Kompilasi resource icon PE Windows (windres)
│   │   ├── assets/                    # Font Plus Jakarta Sans, interface.wav, icon.ico
│   │   └── src/                       # main.rs, sys_integration.rs, icons.rs, views/
│   └── mydiskly-installer/            # Setup Wizard 3 Halaman & Uninstaller Suite
│       ├── Cargo.toml                 # Target biner: MyDiskly-Setup.exe
│       ├── build.rs                   # Resource linker & proteksi fallback stub
│       └── src/main.rs                # Wizard, shortcut senyap, 4-layer force uninstaller
└── assets/                            # Aset visual & logo brand resolusi tinggi
```

---

## 🛠️ Panduan Kompilasi & Build

### Prasyarat Sistem
- **Sistem Operasi**: Windows 10 / Windows 11 (64-bit)
- **Rust Toolchain**: `stable-x86_64-pc-windows-gnu` atau `stable-x86_64-pc-windows-msvc` (Rust 1.75+)
- **LLVM-MinGW / GCC**: Diperlukan untuk penautan API Win32 dan kompilasi resource icon Windows (`windres`)

### Menjalankan Kompilasi Biner

#### Opsi A: Otomasi Pipeline 1-Klik (Disarankan)
Buka PowerShell di folder root repositori, lalu jalankan:
```powershell
.\build.ps1
```
*(Atau jalankan file `build.bat` langsung melalui Command Prompt)*

#### Opsi B: Kompilasi Manual Langkah demi Langkah
```powershell
# 1. Kompilasi Aplikasi Desktop Utama (MyDiskly.exe)
cargo build --release -p mydiskly-app

# 2. Kompilasi Setup Wizard & Installer (MyDiskly-Setup.exe)
cargo build --release -p mydiskly-installer

# 3. Sinkronisasikan Biner Uninstaller
Copy-Item target/release/MyDiskly-Setup.exe target/release/Uninstall.exe -Force
```

Biner hasil kompilasi akan otomatis tersedia di folder `target/release/`:
* `target/release/MyDiskly.exe` (Aplikasi Desktop Utama)
* `target/release/MyDiskly-Setup.exe` (Setup Wizard & Installer Standalone)
* `target/release/Uninstall.exe` (Uninstaller Suite Bersih)

---

## 📄 Lisensi
Proyek ini dilisensikan di bawah **GNU General Public License v3.0 (GPL-3.0)**. Anda bebas menggunakan, mempelajari, memodifikasi, dan mendistribusikan perangkat lunak ini dengan tetap menyertakan atribusi hak cipta dan lisensi terbuka yang sama.

Hak Cipta (C) 2026 **Seroja Labs** & **Darkostepbro**. Seluruh hak cipta dilindungi undang-undang.  
Situs Resmi: [serojalabs.sbs/mydiskly](https://serojalabs.sbs/mydiskly)  
Repositori Kode: [github.com/darkostepbro/mydiskly-desktop-id](https://github.com/darkostepbro/mydiskly-desktop-id)
