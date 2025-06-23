# Section Conclusion: ROS 2 Topics

Di bagian ini, kamu telah belajar bagaimana menggunakan **ROS 2 Topics** sebagai sarana komunikasi antar node dalam ROS 2. Dengan pemahaman ini, kamu sudah bisa mulai membangun aplikasi yang lebih kompleks dan modular!

## Ringkasan Tentang Topics

Sebuah **topic** dalam ROS 2 adalah:

- **Jalur komunikasi bernama** yang digunakan untuk bertukar pesan antar node.
- **Unidirectional**, artinya data hanya mengalir satu arah: dari publisher ke subscriber.
- **Anonim**, publisher tidak mengetahui siapa saja subscribernya, begitu juga sebaliknya.

## Cara Implementasi Topics di ROS 2

1. Buat atau gunakan node yang sudah ada.
2. Tambahkan **publisher** atau **subscriber** sesuai kebutuhan.
3. Pastikan:
   - Nama topik **sama** di kedua sisi
   - Tipe data **cocok** agar komunikasi berhasil
4. Jalankan node-node tersebut, dan komunikasi otomatis akan terjadi.
5. Gunakan perintah CLI `ros2` dan GUI `rqt` untuk membantu debugging dan visualisasi.

### Visualisasi

![conclusion topics](/assets/conclusion_topics.png)

- Nama topik **harus dimulai dengan huruf**.
  > ❌ Contoh tidak valid: `/98.7`  
  > ✅ Contoh valid: `/radio_frequency`

- Topics membantu memisahkan fungsi antar bagian aplikasi (modularitas), sehingga kamu bisa mengembangkan sistem yang fleksibel dan terstruktur.

### 📦 Download Code

Kamu bisa download contoh kode lengkap untuk bagian ini di sini:  
[📥 Download code_end_section_2.zip](code_end_section_2.zip)

| [◀️ Prev: 15 Activity ROS2 Topics](../15_activity_ros2_topics/) | [🏠 Menu Utama](/) | [▶️ Next: ROS2 Service](/section3_services/17_ros2_service/) |
| -------------------------------------------------------------- | ----------------- | ----------------------------------------------------------- |