# ROS 2 Node

Dalam ROS 2, **node** adalah unit eksekusi terkecil dari aplikasi. Setiap node memiliki satu tanggung jawab khusus, dan aplikasi besar biasanya terdiri dari beberapa node yang berjalan secara bersamaan dan saling berkomunikasi.

## Apa Itu Node?

Node dapat dianggap sebagai *komponen modular* dalam sistem robotika. Mereka dikembangkan secara terpisah dan dikelola dalam package.

📌 Contoh:

![Node Communication](/assets/node_communication.png)

- Node A: `Camera driver` — Mengontrol dan mengakses kamera sebagai sensor utama
- Node B: `Image processing` dan `Path correction` — Memproses data dari kamera dan memperbaiki jalur pergerakan robot
- Node C: `Main Control loop` dan `Drivers` — Mengontrol aktuator berdasarkan hasil perencanaan gerak dan koreksi lintasan

## Prinsip Dasar Node

- ✅ **Unik**: Setiap node harus memiliki nama unik.
- ✅ **Ringan**: Satu node hanya fokus pada satu tugas (Single Responsibility).
- ✅ **Berkolaborasi**: Node berkomunikasi menggunakan publisher/subscriber, service, dan action.

## Keuntungan Menggunakan Node

### 1. **Mengurangi Kompleksitas**
Memecah aplikasi ke dalam beberapa node membuat sistem lebih mudah dipahami, dikembangkan, dan diuji.

### 2. **Fault Tolerance**
Jika satu node gagal, node lainnya tetap bisa berjalan, karena mereka tidak bergantung langsung satu sama lain.

### 3. **Language Agnostic**
Kamu bisa menulis node dalam bahasa yang berbeda. Contohnya:
- Node sensor → Python (`rclpy`)
- Node kontrol → C++ (`rclcpp`)
- Kedua node tetap bisa berkomunikasi dengan mulus

## ⚠️ Tips Penamaan Node

- Gunakan nama yang jelas, deskriptif, dan **unik**.
- Hindari nama umum seperti `test_node`, `main`, atau `node1`.

| [◀️ Prev: 03 Create Package](../03_create_package/) | [🏠 Menu Utama](/) | [▶️ Next: 05 Python Node](../05_python_node/) |
| -------------------------------------------------- | ----------------- | -------------------------------------------- |