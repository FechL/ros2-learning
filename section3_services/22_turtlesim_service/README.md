# Experiment on Services with Turtlesim

Setelah bereksperimen dengan **topics**, sekarang kita akan bermain-main dengan **services** di Turtlesim! ROS2 menyediakan beberapa service bawaan untuk turtlesim yang bisa kamu eksplor tanpa perlu menulis kode baru.

## Jalankan Turtlesim

Pertama, pastikan Turtlesim sudah berjalan:

```bash
ros2 run turtlesim turtlesim_node
```

## 🔍 Lihat Daftar Service

Gunakan perintah ini untuk melihat service yang tersedia dari turtlesim:

```bash
ros2 service list
```

Contoh output:
```
/clear
/kill
/reset
/spawn
/turtle1/set_pen
/turtle1/teleport_absolute
/turtle1/teleport_relative
...
```

## Cek Detail Tipe Service

Untuk mengetahui tipe data yang dibutuhkan oleh service tertentu, gunakan:

```bash
ros2 service type /turtle1/teleport_absolute
```

Output:
```
turtlesim/srv/TeleportAbsolute
```

Kemudian untuk melihat struktur request-nya:

```bash
ros2 interface show turtlesim/srv/TeleportAbsolute
```

Output:
```bash
float32 x
float32 y
float32 theta
```

## Beberapa Implementasi Service

### Teleport Absolute

Pindahkan turtle ke posisi tertentu secara instan dengan memanggil service `teleport_absolute`:

```bash
ros2 service call /turtle1/teleport_absolute turtlesim/srv/TeleportAbsolute "{x: 5.0, y: 5.0, theta: 0.0}"
```

Penjelasan:
- `x`, `y`: koordinat posisi baru.
- `theta`: arah sudut (dalam radian, 0 = ke kanan, 1.57 = ke atas, dll).

Turtle akan langsung melompat ke posisi `(5.0, 5.0)`.


### Set Pen (Mengatur Pena Turtle)

Kita bisa juga mengubah warna atau menonaktifkan pena menggunakan service `set_pen`.

```bash
ros2 service call /turtle1/set_pen turtlesim/srv/SetPen "{r: 255, g: 0, b: 0, width: 5, off: 0}"
```

Penjelasan:
- `r, g, b`: warna pena (merah dalam contoh).
- `width`: ketebalan garis.
- `off: 0`: pena aktif (`1` untuk nonaktif).

Sekarang garis yang ditinggalkan turtle akan **tebal dan berwarna merah**!

### Spawn Turtle Baru

Kembalikan turtle (atau buat turtle baru):

```bash
ros2 service call /spawn turtlesim/srv/Spawn "{x: 3.0, y: 3.0, theta: 0.0, name: 'turtle2'}"
```

Kamu bisa spawn lebih dari satu turtle dengan nama berbeda seperti `"turtle2"`, `"turtle3"`, dll.

### Matikan Turtle

Untuk menghapus turtle dari layar, gunakan service `/kill`:

```bash
ros2 service call /kill turtlesim/srv/Kill "{name: 'turtle1'}"
```

| [◀️ Prev:  21 Write a CPP Client](../21_cpp_client/) | [🏠 Menu Utama](/) | [▶️ Next: 23 Activity ROS2 Services](../23_activity_ros2_services/) |
| --------------------------------------------------- | ----------------- | ------------------------------------------------------------------ |