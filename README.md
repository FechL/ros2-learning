# ROS2 (Robot Operating System 2)

**ROS2 (Robot Operating System 2)** adalah framework perangkat lunak open-source yang dirancang khusus untuk pengembangan robot.

ROS2 menyediakan berbagai tools dan library yang bisa digunakan untuk membangun robot. Dengan ROS2, programmer dapat fokus pada pengembangan logika robot tanpa perlu repot membangun infrastruktur dasar seperti **komunikasi antar komponen robot**.

![ros2](/assets/ros2.png)

## Instalasi dan Setup
Untuk instalasi ROS2, ada dua pilihan utama:

***Rekomendasi: Install ROS2 via Ubuntu 22.04 di VirtualBox (Windows Host)***
> Cocok untuk pengguna Windows agar bisa menjalankan ROS2 di lingkungan Linux. Untuk detail [klik di sini](/windows_host/)

***Alternatif: Install langsung di perangkat dengan Linux Ubuntu 22.04***
> Jika kamu sudah menggunakan Ubuntu 22.04 sebagai OS utama, kamu bisa langsung melanjutkan ke step berikutnya.

Next Step:
- 📦 [Install ROS2 Humble](/humble/)
- 🔧 [Install Utility Tools](/utility/)

## 📘 Materi Pembelajaran

### Section 1: Write First ROS2 Program
| Step | Topic                     | Description                                           | Link                                                 |
| ---- | ------------------------- | ----------------------------------------------------- | ---------------------------------------------------- |
| 1    | Build Tool Colcon         | Instalasi dan pengenalan build tool `colcon` di ROS 2 | [klik](/section1_write_ros2/01_build_tool_colcon/)   |
| 2    | Create Workspace          | Pembuatan workspace sebagai dasar pengembangan ROS 2  | [klik](/section1_write_ros2/02_create_workspace/)    |
| 3    | Create Package            | Membuat package menggunakan Python dan C++            | [klik](/section1_write_ros2/03_create_package/)      |
| 4    | ROS2 Node                 | Penjelasan konsep dan arsitektur node dalam ROS 2     | [klik](/section1_write_ros2/04_ros2_node/)           |
| 5    | Write a Node Using Python | Implementasi node ROS 2 menggunakan bahasa Python     | [klik](/section1_write_ros2/05_python_node/)         |
| 6    | Write a Node Using C++    | Implementasi node ROS 2 menggunakan bahasa C++        | [klik](/section1_write_ros2/06_cpp_node/)            |
| 7    | Template for Nodes        | Template OOP untuk membuat node dalam Python dan C++  | [klik](/section1_write_ros2/07_template_node/)       |
| 8    | Section 1 Conclusion      | Kesimpulan dan rangkuman materi pada Section 1        | [klik](/section1_write_ros2/08_section1_conclusion/) |

### Section 2: ROS2 Topics - Publisher and Subsciber
| Step | Topic                               | Description                                                          | Link                                              |
| ---- | ----------------------------------- | -------------------------------------------------------------------- | ------------------------------------------------- |
| 9    | ROS2 Topic                          | Penjelasan konsep topic pada node                                    | [klik](/section2_topics/09_ros2_topic/)           |
| 10   | Write a Python Publisher            | Membuat publisher sederhana menggunakan bahasa Python                | [klik](/section2_topics/10_python_publisher/)     |
| 11   | Write a Python Subscriber           | Membuat subscriber untuk menerima data topic menggunakan Python      | [klik](/section2_topics/11_python_subscriber/)    |
| 12   | Write a C++ Publisher               | Membuat publisher dalam bahasa C++ untuk mengirim data ke topic      | [klik](/section2_topics/12_cpp_publisher/)        |
| 13   | Write a C++ Subscriber              | Membuat subscriber dalam bahasa C++ untuk membaca data dari topic    | [klik](/section2_topics/13_cpp_subscriber/)       |
| 14   | Experiment on Topics with Turtlesim | Bereksperimen dengan topik ROS2 menggunakan simulasi Turtlesim       | [klik](/section2_topics/14_turtlesim_topics/)     |
| 15   | Activity ROS2 Topics                | Aktivitas praktikal untuk memperkuat pemahaman tentang topik di ROS2 | [klik](/section2_topics/15_activity_ros2_topics/) |
| 16   | Section Conclusion                  | Kesimpulan dan rangkuman dari pembelajaran tentang topik di ROS2     | [klik](/section2_topics/16_section2_conclusion/)  |

### Section 3: ROS2 Services - Server and Client

## 🧠 Tips, Tools, and Shortcut

* `ctrl`+`c` untuk menghentikan program pada terminal
* Selalu menjalankan `source ~/.bashrc` sebelum membuat package baru atau node baru.
* Ketika modify file code dan menjalankannya kita perlu build colcon `colcon build --packages-select <your_pkg_name>`.
    ### ROS2 CLI Commands

    | Parameter Dasar | Parameter Lanjutan                                      | Keterangan                                                                                                                                                 |
    | --------------- | ------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | **`topic`**     | `list`                                                  | Menampilkan list topic yang aktif                                                                                                                          |
    |                 | `info /<topic>`                                         | Melihat informasi mengenai topic seperti berapa publisher dan subscribernya                                                                                |
    |                 | `echo /<topic>`                                         | Menampilkan pesan yang dipublikasikan pada topic                                                                                                           |
    |                 | `hz /<topic>`                                           | Menghitung dan menampilkan frekuensi (hertz) dari pesan yang diterima topic                                                                                |
    |                 | `bw /<topic>`                                           | Mengukur bandwidth (throughput) dari pesan yang dikirim pada topic                                                                                         |
    |                 | `pub -r <freq> /<topic> <tipe_msg> "{data pesan}"`      | Mempublikasikan pesan ke topik secara manual. Contoh: `ros2 topic pub -r 10 /robot_news example_interfaces/msg/String "{data: 'hello from terminal'}"`     |
    | **`node`**      | `list`                                                  | Menampilkan list node yang aktif                                                                                                                           |
    |                 | `info /<node>`                                          | Melihat informasi mengenai node                                                                                                                            |
    | **`interface`** | `show <tipe_msg>`                                       | Memberikan informasi detail tentang struktur data dari sebuah antarmuka. Contoh: `ros2 interface show geometry_msg/msg/Twist` (setelah run node turtlesim) |
    | **`bag`**       | `record /<topic>` OR `record -o <name folder> /<topic>` | Merecord isi topic pada topic tertentu sampai stop dan disimpan pada folder                                                                                |
    |                 | `info <folder recorded>`                                | Berisikan informasi record pada folder tertentu                                                                                                            |
    |                 | `play <folder recorder>`                                | Menjalakan isi topic yang sudah terecord pada sebuah folder dengan durasi selama record                                                                    |

* ROS2 Other Tools
     | Topic                        | Description                                                                   | Link                                   |
     | ---------------------------- | ----------------------------------------------------------------------------- | -------------------------------------- |
     | Debug and Monitor Your Nodes | Teknik untuk memantau dan debug node ROS2 secara real-time                    | [klik](/tools/09_debug_monitor_nodes/) |
     | Colcon Tips                  | Tips dan trik dalam menggunakan colcon untuk membangun project ROS2           | [klik](/tools/10_colcon_tips/)         |
     | Rqt and rqt_graph            | Visualisasi dan pemantauan komunikasi antar node dengan `rqt` dan `rqt_graph` | [klik](/tools/11_rqt_and_rqt_graph/)   |
     | Discover Turtlesim           | Eksplorasi dasar penggunaan Turtlesim sebagai simulasi di ROS2                | [klik](/tools/12_discover_turtlesim/)  |
     | Remap a Topic at Runtime     | Cara melakukan remapping topic saat runtime tanpa mengubah kode               | [klik](/tools/13_remap_topic_runtime/) |
## 📚 Referensi Belajar

- [ROS2 For Beginners (ROS Foxy, Humble - 2024)](https://www.udemy.com/course/ros2-for-beginners/)
- [ROS2 for Beginners Level 2 - TF | URDF | RViz | Gazebo](https://www.udemy.com/course/ros2-tf-urdf-rviz-gazebo/)
- [ROS2 for Beginners Level 3 - Advanced Concepts](https://www.udemy.com/course/ros2-advanced-core-concepts/)