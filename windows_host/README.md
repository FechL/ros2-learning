# Install ROS2 via Ubuntu 22.04 di VirtualBox (Windows Host)

Panduan lengkap instalasi ROS2 menggunakan Ubuntu 22.04 LTS di dalam VirtualBox (khusus pengguna Windows).

## 💻 System Requirements (Rekomendasi untuk Windows)
Sebelum instalasi, pastikan perangkat kamu memenuhi spesifikasi minimum berikut agar ROS2 berjalan lancar:

| Komponen           | Rekomendasi Minimum                                        |
| ------------------ | ---------------------------------------------------------- |
| **Prosessor**      | 1.1 GHz 5                                                  |
| **RAM**            | 8 GB (lebih baik 16 GB)                                    |
| **Penyimpanan**    | 40 GB kosong (untuk Ubuntu + ROS2)                         |
| **GPU (opsional)** | NVIDIA / AMD (jika menggunakan simulasi 3D seperti Gazebo) |

## Download Bahan yang Dibutuhkan

Oracle VM VirtualBox: [https://www.virtualbox.org](https://www.virtualbox.org)

Ubuntu 22.04 ISO (Desktop): [https://releases.ubuntu.com/jammy/](https://releases.ubuntu.com/jammy/)

## Buat Mesin Virtual di VirtualBox
Buka VirtualBox → klik **New**

Bagian Name and Operating System, atur:
- **Name**: ubuntu_ros2 (bebas)
- **Load ISO** image dengan **Ubuntu 22.04** yang sudah didownload
- Check **Skip Unattended Installation**

Bagian Hardware, atur:
- **Base Memory**: 4096 MB (rekomendasi 8192 MB)
- **Processor**: 2 core (rekomendasi 4)
- check **Enable EFI**

Bagian Hard Disk, pilih Create **Virtual Hard Disk Now** dan atur:
 - Arahkan ke direktori (rekomendasi SSD)
 - **Size**: minimal 20 GB (rekomendasi 40 GB)
 - **Hard Disk File Type**: VDI (VirtualBox Disk Image)

Finish dan Start

## Instalasi Ubuntu
Enter **Try or Install Ubuntu**

Pilih bahasa → Install Ubuntu → Keyboard Layout (English US)

Pilih opsi antara **Normal Installation** (lebih lama) atau **Minimal Installation**

Pilih opsi **Erase disk and install Ubuntu** (hanya berlaku dalam VM)

Pilih lokasi → Buat username dan password sesuai keinginan

Tunggu hingga instalasi selesai, lalu restart

Open terminal lalu ketik:
<pre lang="markdown">
sudo apt update
sudo apt upgrade
sudo apt autoremove
sudo apt install build-essential gcc make perl dkms python3-pip</pre>

> ini berfungsi untuk mengupdate package-package dan juga menginstall beberapa package yang akan digunakan

## Install Guest Additions (Opsional)

Meningkatkan performa VM dan mengaktifkan fitur copy-paste & folder sharing

1. Saat Ubuntu sudah terbuka, klik menu **Devices** di VirtualBox (atas layar)
2. Pilih **Insert Guest Additions CD Image**
3. Ikuti instruksi di Ubuntu (mungkin butuh password)

Untuk memperbaiki scaling size screen window

1. Pada Menu Bar di atas pilih **Devices→**”**Insert Guest Additions CD image…**” lalu open “**VBox_GAs_…**” di atas Trash dank klik kanan**→**”**Open in Termina**l” dan ketik:

   <pre lang="markdown">
   sudo ./VBoxLinuxAdditions.run
   </pre>

2. Close Ubuntu lalu start Ubuntu lagi.
3. Jika screen belum fix maka ulangi lagi

## Lanjutkan ke Instalasi ROS2
Jika Ubuntu sudah siap, kamu bisa lanjut ke tahapan instalasi ROS2:

- 📦 [Install ROS2 Humble](/humble/)
- 🔧 [Install Utility Tools](/utility/)

 | [🏠 Menu Utama](/) |
 | ----------------- |