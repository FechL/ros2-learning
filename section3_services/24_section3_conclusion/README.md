# Section Conclusion: ROS 2 Services

Di bagian ini, kamu telah mempelajari bagaimana menggunakan **ROS 2 Services** untuk membangun komunikasi client-server antar node. Dengan pemahaman ini, kamu sudah bisa menambahkan kemampuan request/response dalam sistem ROS 2 kamu!

## Ringkasan Tentang Services

Sebuah **service** dalam ROS 2 adalah:

- Jalur komunikasi dua arah antara node **client** dan node **server**.
- Bersifat **synchronous** (menunggu balasan) atau **asynchronous** (non-blocking).
- **Anonim**: client tidak tahu siapa servernya, dan server tidak tahu siapa kliennya — mereka hanya saling bertukar data melalui nama dan tipe service.

## Cara Implementasi Services di ROS 2

1. Buat atau gunakan node yang sudah ada.
2. Tambahkan satu atau lebih **service server** dengan nama unik.
3. Tambahkan node yang akan menjadi **client**, dan pastikan:
   - Nama service **identik** antara client dan server.
   - Tipe service (request + response) juga **identik**.
4. Kamu hanya bisa punya **1 server** per nama service, tapi bisa punya **banyak client**.

> Gunakan CLI `ros2 service` untuk testing, atau buat node client sendiri.

## Kapan Menggunakan Service?

Sebelum menambahkan komunikasi antar node, tanyakan ini:
> “Apakah saya hanya ingin mengirim data, atau saya juga mengharapkan balasan?”

- Jika **hanya mengirim data** → gunakan **Topic**
- Jika **ingin mendapatkan balasan** → gunakan **Service**

Semakin kamu terbiasa, semakin mudah kamu memilih kapan memakai **Topic** atau **Service**.

### Visualisasi

![conclusion services](/assets/conclusion_services.png)

- Nama service mengikuti aturan nama ROS standar (huruf kecil, tanpa spasi, dsb).
- Service cocok untuk **perintah eksplisit** atau **permintaan data** sesaat.
- Berbeda dengan topic, service tidak mengalir terus-menerus — hanya aktif saat diminta.

### 📦 Download Code

Kamu bisa download contoh kode lengkap untuk bagian ini di sini:  
[📥 Download code_end_section_3.zip](code_end_section_3.zip)

| [◀️ Prev: 23 Activity ROS2 Services](../20_activity_ros2_services/) | [🏠 Menu Utama](/) | [▶️ Next: 21 Gazebo (coming soon)](/) |
| ------------------------------------------------------------------ | ----------------- | ------------------------------------ |
