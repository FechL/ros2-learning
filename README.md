# ROS2 (Robot Operating System 2)

## 📌 Introduction

**ROS2 (Robot Operating System 2)** adalah framework perangkat lunak open-source yang dirancang khusus untuk pengembangan robot.

ROS2 menyediakan berbagai tools dan library yang bisa digunakan untuk membangun robot. Dengan ROS2, programmer dapat fokus pada pengembangan logika robot tanpa perlu repot membangun infrastruktur dasar seperti **komunikasi antar komponen robot**.

## 🧩 Instalasi dan Setup
Untuk instalasi ROS2, ada dua pilihan utama:

### Rekomendasi: Install ROS2 via Ubuntu 22.04 di VirtualBox (Windows Host)
Cocok untuk pengguna Windows agar bisa menjalankan ROS2 di lingkungan Linux. Untuk detail [klik disini](/windows_host/)

### Alternatif: Install langsung di perangkat dengan Linux Ubuntu 22.04
Jika kamu sudah menggunakan Ubuntu 22.04 sebagai OS utama, kamu bisa langsung melanjutkan ke step berikutnya.

### Next Step:
- 📦 [Install ROS2 Humble](/humble/)
- 🔧 [Install Utility Tools](/utility/)


## 📘 Materi Pembelajaran

### Section 1: Write First ROS2 Program
| Step | Topic                     | Description                            | Link                                               |
|------|---------------------------|----------------------------------------|----------------------------------------------------|
| 1    | Build Tool Colcon         | Installasi build tool colcon              | [klik](/section1_write_ros2/01_build_tool_colcon/) |
| 2    | Create Workspace          | 	Pembuatan workspace untuk ROS2         | [klik](/section1_write_ros2/02_create_workspace/)  |
| 3    | Create Package            | Membuat package Python dan C++       | [klik](/section1_write_ros2/03_create_package/)    |
| 4    | ROS2 Node                 | Penjelasan konsep node dalam ROS2     | [klik](/section1_write_ros2/04_ros2_node/)         |
| 5    | Write a Node Using Python | 	Membuat node menggunakan Python             | [klik](/section1_write_ros2/05_python_node/)       |
| 6    | Write a Node Using C++    | 	Membuat node menggunakan C++                | [klik](/section1_write_ros2/06_cpp_node/)          |
| 7    | Template for Nodes        | 	Template OOP Python & C++ untuk node | [klik](/section1_write_ros2/07_template_node/)     |
| 8    | Section Conclusion        | 	Kesimpulan dari section 1              | [klik](/section1_write_ros2/08_conclusion/)        |

### Section 2: ROS2 Tools

## 🧠 Tips dan Shortcut

* `ctrl`+`c` untuk menghentikan program pada terminal
* Selalu menjalankan `source ~/.bashrc` sebelum membuat package baru atau node baru.
* Ketika modify file code dan menjalankannya kita perlu build colcon `colcon build --packages-select <your_pkg_name>`.
### ROS2 CLI Commands

| Parameter Dasar | Parameter Lanjutan | Keterangan |
|----------------|-------------------|------------|
| **`topic`** | `list` | Menampilkan list topic yang aktif |
| | `info /<topic>` | Melihat informasi mengenai topic seperti berapa publisher dan subscribernya |
| | `echo /<topic>` | Menampilkan pesan yang dipublikasikan pada topic |
| | `hz /<topic>` | Menghitung dan menampilkan frekuensi (hertz) dari pesan yang diterima topic |
| | `bw /<topic>` | Mengukur bandwidth (throughput) dari pesan yang dikirim pada topic |
| | `pub -r <freq> /<topic> <tipe_msg> "{data pesan}"` | Mempublikasikan pesan ke topik secara manual. Contoh: `ros2 topic pub -r 10 /robot_news example_interfaces/msg/String "{data: 'hello from terminal'}"` |
| **`node`** | `list` | Menampilkan list node yang aktif |
| | `info /<node>` | Melihat informasi mengenai node |
| **`interface`** | `show <tipe_msg>` | Memberikan informasi detail tentang struktur data dari sebuah antarmuka. Contoh: `ros2 interface show geometry_msg/msg/Twist` (setelah run node turtlesim) |
| **`bag`** | `record /<topic>` OR `record -o <name folder> /<topic>` | Merecord isi topic pada topic tertentu sampai stop dan disimpan pada folder |
| | `info <folder recorded>` | Berisikan informasi record pada folder tertentu |
| | `play <folder recorder>` | Menjalakan isi topic yang sudah terecord pada sebuah folder dengan durasi selama record |

## 📚 Referensi Belajar

- [ROS2 For Beginners (ROS Foxy, Humble - 2024)](https://www.udemy.com/course/ros2-for-beginners/)
- [ROS2 for Beginners Level 2 - TF | URDF | RViz | Gazebo](https://www.udemy.com/course/ros2-tf-urdf-rviz-gazebo/)
- [ROS2 for Beginners Level 3 - Advanced Concepts](https://www.udemy.com/course/ros2-advanced-core-concepts/)