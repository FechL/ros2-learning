# Create Package

Dalam ROS 2, **package** adalah unit terkecil dari sebuah proyek. Package bisa berisi program, library, launch file, konfigurasi, dan lainnya. ROS 2 mendukung dua bahasa utama: **Python** dan **C++**.

## 📦 Membuat Package

Pembuatan package dilakukan di dalam folder `src` pada workspace-mu.

### 1. Masuk ke direktori `src`:

```bash
cd ~/ros2_ws/src
```

### 2. Buat package baru:

#### ✅ Untuk **Python**:

```bash
ros2 pkg create ur_name_pkg --build-type ament_python --dependencies rclpy
```

#### ✅ Untuk **C++**:

```bash
ros2 pkg create ur_name_pkg --build-type ament_cmake --dependencies rclcpp
```

> `ur_name_pkg` bisa diganti sesuai nama package yang kamu inginkan.  
> `rclpy` dan `rclcpp` adalah library utama untuk menggunakan ROS 2 di Python dan C++.


## 📁 Struktur Package

Setelah berhasil membuat package, kamu akan mendapatkan struktur direktori seperti:

```
ur_name_pkg/
├── package.xml          # Metadata package
├── CMakeLists.txt       # (Untuk C++) File build system
├── setup.py             # (Untuk Python) File build script
├── ur_name_pkg/         # (Untuk Python) Berisi script dan module utama
└── resource/
```

### 🔧 Edit Metadata dan Dependency

- `package.xml`: Menyimpan informasi metadata package (nama, deskripsi, dependency).
- `CMakeLists.txt`: Digunakan di C++ untuk mendeklarasikan executable, library, dan dependency.

Jika ingin menambahkan library baru atau menyesuaikan deskripsi package, pastikan edit di file tersebut.


## Build Package

Setelah membuat atau mengedit package, kamu harus kembali ke **root workspace** lalu lakukan build:

```bash
cd ~/ros2_ws
```

### Build semua package:

```bash
colcon build
```

### Atau hanya build satu package:

```bash
colcon build --packages-select ur_name_pkg
```

> ⚠️ Jalankan `source install/setup.bash` setelah build agar perubahan dikenali oleh ROS 2.

## Error pip3?

Jika saat build Python package muncul error terkait pip, kamu mungkin belum menginstal `pip3`. Jalankan:

```bash
sudo apt install python3-pip
```
## ✅ Verifikasi Package

Setelah build berhasil, cek apakah package terdaftar:

```bash
ros2 pkg list | grep ur_name_pkg
```
Jika muncul, artinya package berhasil dikenali oleh ROS 2.

| [◀️ Prev: 02 Create Workspace](../02_create_workspace/) | [🏠 Menu Utama](/) | [▶️ Next: 03 ROS2 Node](../04_ros2_node/) |
| ------------------------------------------------------ | ----------------- | ---------------------------------------- |