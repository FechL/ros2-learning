# Write a Python Subscriber Node

Sekarang kita akan membuat **node subscriber** pertama Anda menggunakan **Python** di ROS2. Node ini akan menerima pesan teks dari topik `/robot_news` yang dipublikasikan oleh node lain seperti `robot_news_station`.

## 📁 Buat File Subscriber

Arahkan ke folder:

```bash
ros2_ws/src/my_py_pkg/my_py_pkg/
```

Kemudian buat file Python baru, misalnya:

```bash
touch smartphone.py
chmod +x smartphone.py
```

## Isi Kode Node Subscriber

```python
#!/usr/bin/env python3
import rclpy
from rclpy.node import Node
from example_interfaces.msg import String
 
class SmartphoneNode(Node):
    def __init__(self):
        super().__init__("smartphone")

        self.subscriber_ = self.create_subscription(
            String,             # Tipe pesan
            "robot_news",       # Nama topik
            self.callback_robot_news, # Callback function
            10                  # Ukuran queue
        )

        self.get_logger().info("Smartphone has been started")
    
    def callback_robot_news(self, msg):
        self.get_logger().info(msg.data)
 
def main(args=None):
    rclpy.init(args=args)
    node = SmartphoneNode()
    rclpy.spin(node)
    rclpy.shutdown()
 
if __name__ == "__main__":
    main()
```

## Penjelasan Code
- Menggunakan `example_interfaces/msg/String` sebagai jenis pesan yang akan diterima.
- Node ROS2 dibuat dengan nama `"smartphone"`.
- Subscriber dibuat untuk topik `"robot_news"` dan akan memanggil `callback_robot_news()` saat ada pesan masuk.
- Callback akan menampilkan isi pesan ke terminal/log.

## Setup untuk Build

### Edit `setup.py`

Tambahkan di bagian `entry_points`:

```python
'console_scripts': [
    "smartphone = my_py_pkg.smartphone:main"
]
```

### Edit `package.xml`

Tambahkan dependensi berikut jika belum:

```xml
<depend>example_interfaces</depend>
```

## Build dan Run

Arahkan ke folder utama workspace:

```bash
cd ~/ros2_ws
colcon build --packages-select my_py_pkg
source install/setup.bash
```

Jalankan node subscriber:

```bash
ros2 run my_py_pkg smartphone
```

Pastikan node publisher (`robot_news_station`) juga berjalan. Maka node subscriber ini akan mulai menerima dan menampilkan pesan.

Contoh hasil terminal:

![Screenshot](/assets/terminal_python_subscriber.png)

| [◀️ Prev: 10 Write a Python Publisher](../10_python_publisher/) | [🏠 Menu Utama](/) | [▶️ Next: 12 CPP Publisher](../12_cpp_publisher/) |
| -------------------------------------------------------------- | ----------------- | ------------------------------------------------ |