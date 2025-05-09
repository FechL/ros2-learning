# Create Workspace
Dalam ROS 2, workspace adalah direktori utama tempat kita mengelola dan mengembangkan project ROS. Workspace ini menyimpan semua package, hasil build, dan konfigurasi lainnya agar proyek tetap terstruktur dan modular.

## 📂 Struktur Workspace
Langkah pertama adalah membuat workspace. Kamu bisa menamainya sesuka hati, tapi konvensinya biasanya menggunakan nama ros2_ws.
```bash
mkdir ros2_ws             # Membuat folder utama workspace
cd ros2_ws                # Masuk ke dalam folder workspace
mkdir src                 # Folder src digunakan untuk menyimpan code dan package
colcon build              # Melakukan build pertama kali untuk inisialisasi folder build, install, dan log
```

Setelah build pertama, kamu akan melihat folder tambahan seperti:
- build/ – tempat file hasil kompilasi disimpan.
- install/ – berisi file hasil installasi package setelah build.
- log/ – menyimpan log selama proses build.

> ⚠️ Jalankan colcon build setelah folder src dibuat agar workspace dikenali secara lengkap.

## Source Workspace
Setelah workspace berhasil dibuat dan dibangun, kamu perlu melakukan source agar terminal mengenali environment dan path package ROS 2 di dalam workspace.

Masuk ke direktori install/:
```bash
cd install
```
Lalu pilih salah satu dari dua opsi:
```bash
source local_setup.bash  # Berlaku hanya untuk workspace ini
# ATAU
source setup.bash        # Berlaku lebih global dan mengaktifkan autocomplete
```

Namun, daripada melakukan ini setiap kali membuka terminal, kita bisa menambahkan baris berikut ke file ~/.bashrc:

```bash
source ~/ros2_ws/install/setup.bash
```
Langkah ini akan mengaktifkan workspace secara otomatis setiap kali terminal dibuka, dan juga mengaktifkan fitur autocomplete untuk ROS command.

Cara Menambahkan ke .bashrc:
```bash
gedit ~/.bashrc
```

Tambahkan baris berikut di akhir file:
```bash
source ~/ros2_ws/install/setup.bash
```

Lalu jalankan:
```bash
source ~/.bashrc
```
## ✅ Verifikasi Workspace
Untuk memastikan workspace sudah aktif, kamu bisa mengetik:
```bash
printenv | grep ROS
```

Atau mencoba membangun ulang project yang sudah ditambahkan ke src:
```bash
cd ~/ros2_ws
colcon build
```

| [◀️ Prev: 01 Build Colcon](../01_build_tool_colcon/) | [🏠 Menu Utama](/) | [▶️ Next: 03 Create Package](../03_create_package/) |
| --------------------------------------------------- | ----------------- | -------------------------------------------------- |