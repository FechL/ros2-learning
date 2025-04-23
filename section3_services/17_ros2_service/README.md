# Service di ROS2

Dalam ROS2, **service** digunakan untuk komunikasi **dua arah** antara dua node. Service sangat cocok digunakan ketika kita ingin melakukan **permintaan (request)** dan mendapatkan **jawaban (response)**.

## 📡 Apa Itu Service?

Berbeda dengan topic yang bersifat satu arah dan broadcast, **service** memungkinkan komunikasi **satu-lawan-satu** secara **sinkron** antara client dan server.

- **Client**: Node yang membuat permintaan (request).
- **Server**: Node yang memproses permintaan dan memberikan jawaban (response).

Service cocok digunakan ketika kamu ingin:

- Mengambil data tertentu dari node lain.
- Mengatur suatu parameter atau status.
- Melakukan tindakan satu kali dan menunggu hasilnya.

### Alur Komunikasi Service

![Service Diagram](/assets/service.gif)

### Sifat Komunikasi Service

- **Dua arah (two-way)**: Client kirim permintaan → Server kirim balasan.
- **Sinkron (synchronous)**: Client akan menunggu hingga mendapatkan balasan.
- **Point-to-point**: Hanya terjadi antara satu client dan satu server.

## 📁 Struktur Data

Sebuah service terdiri dari dua bagian utama:

- **Request**: Data yang dikirim oleh client ke server.
- **Response**: Data yang dikirim kembali oleh server ke client.

Contoh service di ROS2:

- `example_interfaces/srv/AddTwoInts`

    ```bash
    int64 a # request
    int64 b
    ---
    int64 sum # response
    ```

## Service Tools

| Perintah Dasar                                     | Keterangan                                                                                                                               |
| -------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| `ros2 service list`                                | Menampilkan semua service aktif.                                                                                                         |
| `ros2 service type /<service>`                     | Melihat tipe service dari nama tertentu.                                                                                                 |
| `ros2 interface show <tipe_srv>`                   | Menampilkan isi struktur data dari service.                                                                                              |
| `ros2 service call /<service> <tipe_srv> "{data}"` | Mengirim permintaan ke service dari terminal. Contoh: `ros2 service call /add_two_ints example_interfaces/srv/AddTwoInts "{a: 2, b: 3}"` |

## Kenapa Gunakan Service?

- Cocok untuk **aksi satu kali** yang butuh jawaban langsung (misalnya: buka gripper, reset sensor, hitung hasil).
- Memastikan bahwa node yang meminta akan mendapatkan jawaban.
- Lebih **terprediksi** daripada topic untuk permintaan berbalas.

## Contoh Kasus Penggunaan Service

- Robot mengirim permintaan untuk **mengisi ulang baterai** dan menunggu konfirmasi.
- Node mengirimkan dua angka ke service untuk dihitung jumlahnya (seperti kalkulator).
- Kamera disuruh **mengambil foto sekali** dan mengembalikannya sebagai response.

| [◀️ Prev: 16 Section 2 Conclusion](/section2_topics/16_section2_conclusion) | [🏠 Menu Utama](/) | [▶️ Next: 18 Write a Python Server](../18_python_server/) |
| -------------------------------------------------------------------------- | ----------------- | -------------------------------------------------------- |