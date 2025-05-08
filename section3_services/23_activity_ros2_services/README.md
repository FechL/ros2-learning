# Activity: ROS2 Services

Saatnya mempraktikkan apa yang sudah kamu pelajari tentang **ROS2 Services**! Kali ini, kamu akan **melanjutkan proyek sebelumnya** dari activity Topics dan menambahkan fitur baru berupa service.

## Struktur Graph

Berikut adalah representasi komunikasi node dan service baru yang akan kamu buat:

![activity_3_services_graph](/assets/activity_3_services_graph.png)

> Kotak biru = Node, Kotak hijau = Topic, Kotak ungu = Service

## Deskripsi Tugas

Proyek sebelumnya sudah memiliki dua node:
- `number_publisher`: menerbitkan angka ke topik `/number`
- `number_counter`: menjumlahkan angka yang diterima, dan menerbitkan hasilnya ke `/number_count`

Sekarang kamu akan **menambahkan satu service** ke node `number_counter`:

**Tujuan**

Menambahkan **service server** di `number_counter` untuk mengatur ulang (`reset`) counter menjadi 0.

**Spesifikasi**

- **Nama Service:** `/reset_counter`
- **Tipe:** `example_interfaces/srv/SetBool`
- **Perilaku:** 
  - Jika request `data: true`, maka counter direset ke 0
  - Respon akan berisi success = true, dan message sesuai keinginan (misalnya: `"Counter has been reset"`)

Kamu bisa memanggil service ini langsung dari terminal, atau membuat client node sendiri untuk latihan tambahan.

## Contoh Pemanggilan Service

```bash
ros2 service call /reset_counter example_interfaces/srv/SetBool "{data: true}"
```

Gunakan perintah ini untuk melihat isi dari service:

```bash
ros2 interface show example_interfaces/srv/SetBool
```

Outputnya akan menunjukkan struktur berikut:

```
bool data
---
bool success
string message
```

## Output yang Diharapkan

Saat service dipanggil, terminal dari `number_counter` akan menampilkan pesan bahwa counter telah direset. Nilai yang diterbitkan ke `/number_count` akan mulai lagi dari 0.

```bash
ros2 topic echo /number_count
```

Sebelum reset:
```
data: 42
```

Setelah reset:
```
data: 0
```

## 💡 Tips Pengerjaan

1. Gunakan kembali node `number_counter` dan tambahkan service server di dalam kelas atau fungsi yang sama.
2. Jangan lupa untuk mengecek isi request `SetBool` dan memberikan response dengan `success = true` dan `message` yang sesuai.
3. Jika ingin lebih menantang, kamu bisa membuat node client `reset_counter_client` menggunakan Python atau C++.

## Answer (spoiler)

Jawaban tersedia di folder kode pada direktori ini.

| [◀️ Prev: 15 Activity ROS2 Topics](../15_activity_ros2_topics/) | [🏠 Menu Utama](/) | [▶️ Next: 17 Services in Depth](../17_services_in_depth/) |
| -------------------------------------------------------------- | ----------------- | -------------------------------------------------------- |