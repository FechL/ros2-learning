# ROS2 (Robot Operating System 2)

**ROS2 (Robot Operating System 2)** adalah framework perangkat lunak open-source yang dirancang khusus untuk pengembangan robot.

ROS2 menyediakan berbagai tools dan library yang bisa digunakan untuk membangun robot. Dengan ROS2, programmer dapat fokus pada pengembangan logika robot tanpa perlu repot membangun infrastruktur dasar seperti **komunikasi antar komponen robot**.

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
| Step | Topic                               | Description                                                  | Link                                              |
| ---- | ----------------------------------- | ------------------------------------------------------------ | ------------------------------------------------- |
| 9    | ROS2 Topic                          | Penjelasan konsep topic pada node                            | [klik](/section2_topics/09_ros2_topic/)           |
| 10   | Write a Python Publisher            | Membuat publisher menggunakan Python                         | [klik](/section2_topics/10_python_publisher/)     |
| 11   | Write a Python Subscriber           | Membuat subscriber menggunakan Python                        | [klik](/section2_topics/11_python_subscriber/)    |
| 12   | Write a C++ Publisher               | Membuat publisher menggunakan C++                            | [klik](/section2_topics/12_cpp_publisher/)        |
| 13   | Write a C++ Subscriber              | Membuat subscriber menggunakan C++                           | [klik](/section2_topics/13_cpp_subscriber/)       |
| 14   | Experiment on Topics with Turtlesim | Bereksperimen topic ROS2 menggunakan simulasi Turtlesim      | [klik](/section2_topics/14_turtlesim_topics/)     |
| 15   | Activity ROS2 Topics                | Aktivitas praktikal untuk memperkuat pemahaman topic di ROS2 | [klik](/section2_topics/15_activity_ros2_topics/) |
| 16   | Section 2 Conclusion                | Kesimpulan dan rangkuman materi pada Section 2               | [klik](/section2_topics/16_section2_conclusion/)  |

### Section 3: ROS2 Services - Server and Client

| Step | Topic                                 | Description                                                    | Link                                                  |
| ---- | ------------------------------------- | -------------------------------------------------------------- | ----------------------------------------------------- |
| 17   | ROS2 Service                          | Penjelasan konsep service pada node ROS2                       | [klik](/section3_services/17_ros2_service/)           |
| 18   | Write a Python Server                 | Membuat service server menggunakan Python                      | [klik](/section3_services/18_python_server/)          |
| 19   | Write a Python Client                 | Membuat service client menggunakan Python                      | [klik](/section3_services/19_python_client/)          |
| 20   | Write a C++ Server                    | Membuat service server menggunakan C++                         | [klik](/section3_services/20_cpp_server/)             |
| 21   | Write a C++ Client                    | Membuat service client menggunakan C++                         | [klik](/section3_services/21_cpp_client/)             |
| 22   | Experiment on Services with Turtlesim | Bereksperimen dengan service ROS2 untuk latihan langsung       | [klik](/section3_services/22_experiment_services/)    |
| 23   | Activity ROS2 Services                | Aktivitas praktikal untuk memperkuat pemahaman service di ROS2 | [klik](/section3_services/23_activity_ros2_services/) |
| 24   | Section 3 Conclusion                  | Kesimpulan dan rangkuman materi pada Section 3                 | [klik](/section3_services/24_section3_conclusion/)    |

## Tips, Tools, and Shortcut

* `ctrl`+`c` untuk menghentikan program pada terminal
* Selalu menjalankan `source ~/.bashrc` sebelum membuat package baru atau node baru.
* Ketika modify file code dan menjalankannya kita perlu build colcon `colcon build --packages-select <your_pkg_name>`.
    ### ROS2 CLI Commands

    | Parameter Dasar | Parameter Lanjutan                                      | Keterangan                                                                                                                                                                        |
    | --------------- | ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | **`topic`**     | `list`                                                  | Menampilkan daftar topik yang aktif.                                                                                                                                              |
    |                 | `info /<topic>`                                         | Menampilkan informasi tentang topik seperti jumlah publisher dan subscriber.                                                                                                      |
    |                 | `echo /<topic>`                                         | Menampilkan pesan yang dipublikasikan pada topik secara real-time.                                                                                                                |
    |                 | `hz /<topic>`                                           | Menghitung dan menampilkan frekuensi (hertz) dari pesan yang diterima pada topik.                                                                                                 |
    |                 | `bw /<topic>`                                           | Mengukur bandwidth (throughput) dari pesan yang dikirim pada topik.                                                                                                               |
    |                 | `pub -r <freq> /<topic> <tipe_msg> "{data}"`            | Mempublikasikan pesan ke topik secara manual. Contoh: `ros2 topic pub -r 10 /robot_news example_interfaces/msg/String "{data: 'hello from terminal'}"`                            |
    | **`service`**   | `list`                                                  | Menampilkan daftar service yang aktif.                                                                                                                                            |
    |                 | `type /<service>`                                       | Menampilkan tipe service dari nama service yang dipilih.                                                                                                                          |
    |                 | `call /<service> <tipe_srv> "{data}"`                   | Memanggil service secara manual. Contoh: `ros2 service call /reset_counter example_interfaces/srv/SetBool "{data: true}"`                                                         |
    |                 | `info /<service>`                                       | Menampilkan detail informasi tentang service, termasuk tipe request dan response.                                                                                                 |
    | **`node`**      | `list`                                                  | Menampilkan daftar node yang aktif.                                                                                                                                               |
    |                 | `info /<node>`                                          | Menampilkan informasi tentang node, termasuk publisher, subscriber, service, dll.                                                                                                 |
    |                 | `list_endpoints /<node>`                                | Menampilkan daftar endpoint (topik dan service) yang digunakan oleh node.                                                                                                         |
    | **`interface`** | `show <tipe_msg_or_srv>`                                | Menampilkan struktur data lengkap dari sebuah pesan atau service. Contoh: `ros2 interface show geometry_msgs/msg/Twist` atau `ros2 interface show example_interfaces/srv/SetBool` |
    | **`bag`**       | `record /<topic>` OR `record -o <folder_name> /<topic>` | Merekam isi topik ke dalam sebuah folder sampai dihentikan secara manual.                                                                                                         |
    |                 | `info <folder_name>`                                    | Menampilkan informasi tentang rekaman yang ada dalam folder tertentu.                                                                                                             |
    |                 | `play <folder_name>`                                    | Memutar ulang data topik yang sudah direkam dalam folder.                                                                                                                         |


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