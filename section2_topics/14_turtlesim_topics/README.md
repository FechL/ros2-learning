# Experiment on Topics with Turtlesim

Sekarang saatnya melakukan **eksperimen langsung** dengan **Turtlesim** menggunakan topik! Kita akan menggunakan perintah `ros2 topic pub` untuk mengontrol pergerakan turtle dengan **publikasi manual ke topik** tertentu.

## Run Turtlesim

> bagi yang belum tahu turtlesim: [Discover Turtlesim](/tools/12_discorver_turtlesim)

Langkah pertama, jalankan node Turtlesim:

```bash
ros2 run turtlesim turtlesim_node
```

### Kirim Perintah ke Topik

Sekarang kita akan mengontrol turtle dengan mem-publish pesan ke topik `/turtle1/cmd_vel` menggunakan pesan dari tipe `geometry_msgs/msg/Twist`.

```bash
ros2 topic pub -r 2 /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 1.0}, angular: {z: 1.0}}"
```

Penjelasan:
- `-r 2`: mengirim pesan 2 kali per detik.
- `linear.x = 1.0`: menggerakkan turtle ke depan.
- `angular.z = 1.0`: membuat turtle berputar.
- Kombinasi ini menghasilkan gerakan **melingkar**.

### Visual Output

Setelah menjalankan perintah di atas, turtle akan mulai bergerak **melingkar** seperti yang terlihat di bawah ini:

![turtlesim circle](/assets/turtlesim_circle.png)

Jadi dengan menggunakan perintah `ros2 topic pub`, Anda bisa mengontrol node dengan cepat tanpa perlu membuat node baru. Ini sangat berguna untuk testing, debugging, atau eksplorasi awal topik komunikasi di ROS2.

| [◀️ Prev: 13 Write a C++ Subscriber](../13_cpp_subscriber/) | [🏠 Menu Utama](/) | [▶️ Next: 15 Activity ROS2 Topics](../15_activity_ros2_topics/) |
| ---------------------------------------------------------- | ----------------- | -------------------------------------------------------------- |