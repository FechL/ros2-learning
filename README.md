# ROS2 (Robot Operating System 2)

## Introduction

**ROS2 (Robot Operating System 2)** adalah framework perangkat lunak open-source yang dirancang khusus untuk pengembangan robot.

ROS2 menyediakan berbagai tools dan library yang bisa digunakan untuk membangun robot. Dengan ROS2, programmer dapat fokus pada pengembangan logika robot tanpa perlu repot membangun infrastruktur dasar seperti **komunikasi antar komponen robot**.

## Instalasi dan Setup
Pemakaian ROS2 disarankan menggunakan [Ubuntu](https://ubuntu.com/#get-ubuntu) versi 22. Untuk menjalankan OS Ubuntu bisa melalui [Oracle VM VirtualBox](https://www.virtualbox.org).

Setelah install VirtualBox, tekan **“New”** dan setup sesuai yang diinginkan. Untuk pemasangan iso file bisa click setting pada setup tersebut lalu **Storage→VBoxGuestAdditions.iso** dan choose file iso ubuntu yang telah didownload. Click start untuk run.

next step:
1. Setup Ubuntu VM VirtualBox [klik disini](/ubuntu/)
2. Install ROS2 Humble [klik disini](/humble/)
3. Utility Tools [klik disini](/utility/)

## Materi

### Section 1: Write First ROS2 Program
| Step | Topic                     | Description                            | Link                                               |
|------|---------------------------|----------------------------------------|----------------------------------------------------|
| 1    | Build Tool Colcon         | install build tool colcon              | [klik](/section1_write_ros2/01_build_tool_colcon/) |
| 2    | Create Workspace          | pembuatan workspace untuk ROS2         | [klik](/section1_write_ros2/02_create_workspace/)  |
| 3    | Create Package            | pembuatan package python dan c++       | [klik](/section1_write_ros2/03_create_package/)    |
| 4    | ROS2 Node                 | penjelasan mengenai node pada ROS2     | [klik](/section1_write_ros2/04_ros2_node/)         |
| 5    | Write a Node Using Python | Membuat node dengan python             | [klik](/section1_write_ros2/05_python_node/)       |
| 6    | Write a Node Using C++    | Membuat node dengan c++                | [klik](/section1_write_ros2/06_cpp_node/)          |
| 7    | Template for Nodes        | template OOP untuk node python dan c++ | [klik](/section1_write_ros2/07_template_node/)     |
| 8    | Section Conclusion        | kesimpulan dari seksi ini              | [klik](/section1_write_ros2/08_conclusion/)        |


## Tips

* `ctrl`+`c` untuk menghentikan program pada terminal
* Selalu menjalankan `source ~/.bashrc` sebelum membuat package baru atau node baru.
* Ketika modify file code dan menjalankannya kita perlu build colcon `colcon build --packages-select <your_pkg_name>`.
* ros2 other commands:

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

## Source

- Udemy: [ROS2 For Beginners (ROS Foxy, Humble - 2024)](https://www.udemy.com/course/ros2-for-beginners/)
- Udemy: [ROS2 for Beginners Level 2 - TF | URDF | RViz | Gazebo](https://www.udemy.com/course/ros2-tf-urdf-rviz-gazebo/)
- Udemy: [ROS2 for Beginners Level 3 - Advanced Concepts](https://www.udemy.com/course/ros2-advanced-core-concepts/)