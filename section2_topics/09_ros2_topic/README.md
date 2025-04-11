# Topic di ROS2

Dalam ROS2, **topic** berfungsi sebagai jalur komunikasi satu arah antara node-node yang ada. Topik memungkinkan pengiriman data secara **asinkron** dan **berkelanjutan**.

## 📡 Apa Itu Topic?

**Topic** dapat diibaratkan seperti sebuah **bus data**, di mana banyak node bisa ikut menumpang:

- **Publisher**: Node yang **mengirim (publish)** data ke suatu topik.
- **Subscriber**: Node yang **menerima (subscribe)** data dari topik tersebut.

> ROS2 tidak membatasi jumlah publisher atau subscriber dalam satu topik.

## Sifat Komunikasi Topic

- **Satu arah (one-way)**: Publisher hanya bisa mengirim, Subscriber hanya bisa menerima.
- **Broadcast**: Semua subscriber akan menerima data dari publisher yang sama.
- **Asynchronous**: Publisher tidak peduli apakah ada subscriber atau tidak. Data tetap dikirim.

## Alur Komunikasi Topic

![Topic](/assets/topic.gif)

## Kenapa Topic Penting?

- **Desain modular**: Setiap bagian sistem bisa dikembangkan secara terpisah.
- **Efisien**: Node hanya menangani tugas tertentu dan berkomunikasi lewat topik.
- **Fleksibel**: Node bisa ditambahkan atau dihapus tanpa mengganggu sistem secara keseluruhan.


## Contoh Kasus Penggunaan Topic

- Robot mobile mengirimkan data posisi (`/odom`) ke topik.
- Sensor lidar mengirim data ke topik (`/scan`).
- Kamera mengirim gambar ke topik (`/image_raw`).
- Node lain membaca data tersebut untuk diproses lebih lanjut.

## 📁 Struktur Data

Semua data yang dikirim lewat topic harus memiliki **tipe pesan** tertentu dari ROS2 seperti:

- `std_msgs/msg/String` – untuk teks.
- `std_msgs/msg/Int32` – untuk bilangan bulat.
- `sensor_msgs/msg/LaserScan` – untuk data sensor lidar.
- `geometry_msgs/msg/Twist` – untuk pergerakan robot (linear + angular).

| [◀️ Prev: 08 Section 1 Conclusion](/section1_write_ros2/08_section1_conclusion/) | [🏠 Menu Utama](/) | [▶️ Next: 10 Write a Python Publisher](../10_python_publisher/) |
| ------------------------------------------------------------------------------- | ----------------- | -------------------------------------------------------------- |