# 📥 Install ROS2 via Ubuntu 22.04 di VirtualBox (Windows Host)

Panduan lengkap instalasi ROS2 menggunakan Ubuntu 22.04 LTS di dalam VirtualBox (khusus pengguna Windows).

## 💻 System Requirements (Rekomendasi untuk Windows)
Sebelum instalasi, pastikan perangkat kamu memenuhi spesifikasi minimum berikut agar ROS2 berjalan lancar:

| Komponen      | Rekomendasi Minimum                                     |
|---------------|----------------------------------------------------------|
| **CPU**       | Intel Core i5 Gen 8 / AMD Ryzen 5                        |
| **RAM**       | 8 GB (lebih baik 16 GB)                                  |
| **Penyimpanan** | 40 GB kosong (untuk Ubuntu + ROS2)                     |
| **GPU (opsional)** | NVIDIA / AMD (jika menggunakan simulasi 3D seperti Gazebo) |

## 1. Download Bahan yang Dibutuhkan
### a. Oracle VM VirtualBox
- Unduh dari: [https://www.virtualbox.org](https://www.virtualbox.org)
- Install di Windows seperti biasa

### b. Ubuntu 22.04 ISO
- Download dari: [https://ubuntu.com/#get-ubuntu](https://ubuntu.com/#get-ubuntu)
- Gunakan versi **Desktop**, bukan Server

## 2. Buat Mesin Virtual di VirtualBox
### a. Buat VM Baru
1. Buka VirtualBox → klik **New**
2. Isi:
   - **Name**: `ubuntu_ros2`
   - **Type**: `Linux`
   - **Version**: `Ubuntu (64-bit)`
3. Klik **Next**

### b. Atur Memori dan Prosesor
- **Memory Size**: 4096 MB (rekomendasi 8192 MB)
- Setelah VM dibuat → klik kanan → **Settings → System**:
  - **Processor**: atur 2 core (rekomendasi 4)
  - **Motherboard**: centang **Enable EFI**

### c. Buat Hard Disk Virtual
- Pilih: **VDI (VirtualBox Disk Image)**
- Tipe: **Dynamically allocated**
- Ukuran: minimal **30 GB** (rekomendasi 50 GB)

### d. Masukkan File ISO
- Settings → **Storage** → klik ikon CD di Controller IDE
- Masukkan file `.iso` Ubuntu 22.04

## 3. Instalasi Ubuntu
1. Klik **Start** untuk menjalankan VM
2. Ikuti langkah-langkah instalasi Ubuntu:
   - Pilih bahasa → **Install Ubuntu**
   - Gunakan opsi: *Erase disk and install Ubuntu* (hanya berlaku dalam VM)
   - Buat username dan password sesuai keinginan
3. Tunggu hingga instalasi selesai, lalu restart

## 4. Install Guest Additions (Opsional)
> Meningkatkan performa VM dan mengaktifkan fitur copy-paste & folder sharing

1. Saat Ubuntu sudah terbuka, klik menu **Devices** di VirtualBox (atas layar)
2. Pilih **Insert Guest Additions CD Image**
3. Ikuti instruksi di Ubuntu (mungkin butuh password)


## 5. Lanjutkan ke Instalasi ROS2
Jika Ubuntu sudah siap, kamu bisa lanjut ke tahapan instalasi ROS2:

- 📦 [Install ROS2 Humble](/humble/)
- 🔧 [Install Utility Tools](/utility/)

## 🧑‍💻 Notes
- VM ini hanya digunakan sebagai lingkungan kerja ROS2
- Jika ingin lebih performa tinggi, bisa dual boot Ubuntu + Windows (lanjutan dari ini)
- Dokumentasi ini ditujukan untuk pemula atau peserta pelatihan robotik berbasis ROS2

## ❓ Butuh Bantuan?
Jika kamu mengalami kendala, jangan ragu bertanya melalui forum, komunitas, atau mentor kamu.
