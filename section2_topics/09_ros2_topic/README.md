# Topic di ROS2

Dalam ROS2, **topic** berfungsi sebagai jalur komunikasi satu arah antara node-node yang ada. Topik memungkinkan pengiriman data secara **asinkron** dan **berkelanjutan**.

## 📡 Apa Itu Topic?

Topik dalam ROS 2 berperan seperti jalur komunikasi bersama (bus) yang memungkinkan pertukaran data antar node. Mekanisme komunikasi ini bersifat terbuka, artinya semua node dapat secara bebas mengirim (publish) atau menerima (subscribe) data melalui topik yang sama tanpa batasan. Selama sebuah node terhubung ke topik tersebut, ia bisa terus berkomunikasi dengan node lain melalui topik yang sama.

Topic dapat diibaratkan seperti sebuah **bus data**, di mana banyak node bisa ikut menumpang:

- **Publisher**: Node yang **mengirim (publish)** data ke suatu topik.
- **Subscriber**: Node yang **menerima (subscribe)** data dari topik tersebut.

> ROS2 tidak membatasi jumlah publisher atau subscriber dalam satu topik.

### Alur Komunikasi Topic

![Topic](/assets/topic.gif)

### Sifat Komunikasi Topic

- **Satu arah (one-way)**: Publisher hanya bisa mengirim, Subscriber hanya bisa menerima.
- **Broadcast**: Semua subscriber akan menerima data dari publisher yang sama.
- **Asynchronous**: Publisher tidak peduli apakah ada subscriber atau tidak. Data tetap dikirim.

## 📁 Struktur Data

Semua data yang dikirim lewat topic harus memiliki **tipe pesan** tertentu dari ROS2 seperti:

- `std_msgs/msg/String` – untuk teks.
- `std_msgs/msg/Int32` – untuk bilangan bulat.
- `sensor_msgs/msg/LaserScan` – untuk data sensor lidar.
- `geometry_msgs/msg/Twist` – untuk pergerakan robot (linear + angular).

## Topic Tools

| Parameter Dasar | Parameter Lanjutan                                 | Keterangan                                                                                                                                             |
| --------------- | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **`topic`**     | `list`                                             | Menampilkan list topic yang aktif                                                                                                                      |
|                 | `info /<topic>`                                    | Melihat informasi mengenai topic seperti berapa publisher dan subscribernya                                                                            |
|                 | `echo /<topic>`                                    | Menampilkan pesan yang dipublikasikan pada topic                                                                                                       |
|                 | `hz /<topic>`                                      | Menghitung dan menampilkan frekuensi (hertz) dari pesan yang diterima topic                                                                            |
|                 | `bw /<topic>`                                      | Mengukur bandwidth (throughput) dari pesan yang dikirim pada topic                                                                                     |
|                 | `pub -r <freq> /<topic> <tipe_msg> "{data pesan}"` | Mempublikasikan pesan ke topik secara manual. Contoh: `ros2 topic pub -r 10 /robot_news example_interfaces/msg/String "{data: 'hello from terminal'}"` |

## Kenapa Topic Penting?

- **Desain modular**: Setiap bagian sistem bisa dikembangkan secara terpisah.
- **Efisien**: Node hanya menangani tugas tertentu dan berkomunikasi lewat topik.
- **Fleksibel**: Node bisa ditambahkan atau dihapus tanpa mengganggu sistem secara keseluruhan.


## Contoh Kasus Penggunaan Topic

- Robot mobile mengirimkan data posisi (`/odom`) ke topik.
- Sensor lidar mengirim data ke topik (`/scan`).
- Kamera mengirim gambar ke topik (`/image_raw`).
- Node lain membaca data tersebut untuk diproses lebih lanjut.

| [◀️ Prev: 08 Section 1 Conclusion](/section1_write_ros2/08_section1_conclusion/) | [🏠 Menu Utama](/) | [▶️ Next: 10 Write a Python Publisher](../10_python_publisher/) |
| ------------------------------------------------------------------------------- | ----------------- | -------------------------------------------------------------- |