
# Write a Python Publisher Node

Sekarang kita akan membuat **node publisher** pertama Anda menggunakan **Python** di ROS2. Node ini akan mengirimkan pesan teks secara berkala ke sebuah topik bernama `/robot_news`.

## 📁 Buat File Publisher

Arahkan ke folder:

```bash
ros2_ws/src/my_py_pkg/my_py_pkg/
```

Kemudian buat file Python baru, misalnya:

```bash
touch robot_news_station.py
chmod +x robot_news_station.py
```

## Isi Kode Node Publisher

```python
#!/usr/bin/env python3
import rclpy
from rclpy.node import Node
from example_interfaces.msg import String

class RobotNewStation(Node):
    def __init__(self):
        super().__init__("robot_news_station")

        self.robot_name_ = "C3PO"
        self.publisher_ = self.create_publisher(String, "robot_news", 10)
        self.timer_ = self.create_timer(0.5, self.publish_news)
        self.get_logger().info("Robot News Station has been started")
    
    def publish_news(self):
        msg = String()
        msg.data = f"Hi, this is {self.robot_name_} from the Robot News Station."
        self.publisher_.publish(msg)

def main(args=None):
    rclpy.init(args=args)
    node = RobotNewStation()
    rclpy.spin(node)
    rclpy.shutdown()

if __name__ == "__main__":
    main()
```

Penjelasan Code
- Anda menggunakan `example_interfaces/msg/String` sebagai jenis pesan.
- Node ROS2 dibuat dengan nama "robot_news_station".
- Publisher dibuat untuk topik "robot_news" dengan jenis pesan String.
- Node ini mengirim pesan string ke topik `/robot_news`.
- Setiap 0.5 detik, node mengirim pesan ke topik tersebut.


## Setup untuk Build

### Edit `setup.py`

Tambahkan di bagian `entry_points`:

```python
'console_scripts': [
    "robot_news_station = my_py_pkg.robot_news_station:main"
]
```

### Edit `package.xml`

Tambahkan dependensi berikut:

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

Kemudian jalankan node:

```bash
ros2 run my_py_pkg robot_news_station
```

Contoh hasil terminal:
![Screenshot](/assets/terminal_python_node.png)

| [◀️ Prev: 09 ROS2 Topic](../09_ros2_topic/) | [🏠 Menu Utama](/) | [▶️ Next: 11 Write a Python Subsciber](../11_python_subscriber/) |
| ------------------------------------------ | ----------------- | --------------------------------------------------------------- |