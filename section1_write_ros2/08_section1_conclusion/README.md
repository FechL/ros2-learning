# Section Conclusion

Di bagian ini, kamu telah mempelajari cara membuat node pertama di **ROS2**, baik menggunakan **Python** maupun **C++**. Ini adalah landasan penting dalam membangun aplikasi ROS.

## Apa itu Node?

Node adalah **subprogram** dalam sebuah aplikasi ROS. Setiap node:
- Bertanggung jawab **untuk satu tugas spesifik**.
- Berkomunikasi dengan node lain melalui **Topic**, **Service**, dan **Parameter**.

## Sebelum Membuat Node

Pastikan kamu sudah melakukan langkah berikut:

1. **Membuat Workspace ROS2**  
   Folder kerja utama yang akan menampung semua package kamu.
2. **Membuat Package** (Python / C++)  
   Tempat untuk menyimpan kode program (node) kamu.

## Membuat Node

Gunakan client library yang sesuai:

- `rclpy` untuk **Python**
- `rclcpp` untuk **C++**

Library ini menyediakan:
- Logger
- Publisher/Subscriber
- Timer, dan lain-lain

Setelah menulis node:

- Untuk C++, lakukan **compile** (`colcon build`)
- Untuk Python, cukup **install** saja (`colcon build` juga, tapi tanpa compile)

Kemudian jalankan dengan:

```bash
ros2 run <package_name> <executable_name>
```

### Visualisasi

Berikut adalah ilustrasi struktur node dalam package:

![ROS2 Package Architecture](/assets/ros2_package_architecture.png)


### 📦 Download Code

Kamu bisa download contoh kode lengkap untuk bagian ini di sini:  
[📥 Download code_end_section_1.zip](code_end_section_1.zip)

| [◀️ Prev: 07 Template Node](../07_template_node/) | [🏠 Menu Utama](/) | [▶️ Next: 09 ROS2 Topic](/section2_topics/09_ros2_topic/) |
| ------------------------------------------------ | ----------------- | -------------------------------------------------------- |