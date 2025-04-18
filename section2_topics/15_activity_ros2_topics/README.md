# Activity: ROS2 Topics

Saatnya mempraktikkan apa yang sudah kamu pelajari di section **ROS2 Topics** sebelumnya. Kali ini, kamu akan membuat sistem kecil yang terdiri dari dua node yang berkomunikasi melalui dua topik.

## Struktur Graph

Berikut adalah representasi graph komunikasi antar-node dan topik:

![activity 1 graph](/assets/activity_1_graph.png)

> Kotak biru = Node, Kotak hijau = Topic

## Deskripsi Tugas

Kamu akan membuat **dua node** dari awal:
- Node pertama hanya memiliki **1 publisher**
- Node kedua memiliki **1 subscriber** dan **1 publisher**

Rincian node:
- **Node `number_publisher`**:
  - Menerbitkan angka tetap (misalnya: `2`) ke topik `/number`
  - Menggunakan pesan tipe `example_interfaces/msg/Int64`
- **Node `number_counter`**:
  - Berlangganan ke topik `/number`
  - Memiliki variabel penghitung `counter`
  - Setiap menerima angka baru, angka tersebut ditambahkan ke `counter`
  - Menerbitkan hasil penjumlahan ke topik `/number_count`

Bebas menggunakan **Python** atau **C++**. Bahkan, kamu bisa mencampurnya.

## Output yang Diharapkan

Setelah semuanya berjalan, coba jalankan perintah berikut di terminal:

```bash
ros2 topic echo /number_count
```

Hasilnya akan terlihat seperti ini:

![activity 1 output](/assets/activity_1_output.png)

## 💡 Tips Pengerjaan

1. Buat node `number_publisher` terlebih dahulu. Pastikan publisher bekerja dengan baik menggunakan `ros2 topic echo`.
2. Lanjutkan dengan node `number_counter`, mulai dari subscriber-nya.
3. Terakhir, tambahkan publisher pada `number_counter` untuk menerbitkan hasil counter.

Gunakan perintah berikut untuk melihat isi struktur pesan `Int64`:

```bash
ros2 interface show example_interfaces/msg/Int64
```

Dalam `number_counter`, **publisher sebaiknya langsung dipanggil dari dalam callback subscriber**.

## Answer (spoiler)

Code jawaban terdapat pada file di folder ini.

| [◀️ Prev: 14 Experiment on Topics with Turtlesim](../14_turtlesim_topics/) | [🏠 Menu Utama](/) | [▶️ Next: 16 Section 2 Conclusion](../16_section2_conclusion/) |
| ------------------------------------------------------------------------- | ----------------- | ------------------------------------------------------------- |