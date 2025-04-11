# Write a Node Using Python

ROS2 memungkinkan kita membuat node menggunakan bahasa Python. Di bawah ini adalah panduan lengkapnya.

## 📁 Struktur Folder

Arahkan terminal ke folder berikut:

```bash
cd ~/ros2_ws/src/my_py_pkg/my_py_pkg
```

Buat file node:

```bash
touch my_first_node.py
```

## Minimal Python Node

Buka file `my_first_node.py` dan masukkan kode berikut:

```python
#!/usr/bin/env python3
import rclpy
from rclpy.node import Node

def main(args=None):
    rclpy.init(args=args)
    node = Node("py_test_node")
    rclpy.spin(node)
    node.get_logger().info("Hello ROS2")
    rclpy.shutdown()

if __name__ == "__main__":
    main()
```

### Buat File Menjadi Executable

```bash
chmod +x my_first_node.py
```

Menjalankannya langsung (tidak disarankan untuk produksi):

```bash
./my_first_node.py
```

Namun, **cara terbaik adalah melalui instalasi package**.

### Instalasi via `setup.py`

Buka file `setup.py`, dan cari bagian `entry_points` lalu ubah seperti ini:

```python
entry_points={
    'console_scripts': [
        'py_node = my_py_pkg.my_first_node:main'
    ],
},
```

### Build Package

Kembali ke folder workspace:

```bash
cd ~/ros2_ws
colcon build --packages-select my_py_pkg
```

Jika berhasil, file Python Anda akan tersedia di:

```
install/my_py_pkg/lib/my_py_pkg/py_node
```

### Menjalankan Node

```bash
source install/setup.bash
ros2 run my_py_pkg py_node
```

## Write Node with OOP (Class)

Contoh Node Python menggunakan class (lebih fleksibel):

```python
#!/usr/bin/env python3
import rclpy
from rclpy.node import Node

class MyNode(Node):
    def __init__(self):
        super().__init__("py_test")
        self.counter_ = 0
        self.get_logger().info("Hello ROS2!!")
        self.create_timer(0.5, self.timer_callback)

    def timer_callback(self):
        self.counter_ += 1
        self.get_logger().info(f"Hello {self.counter_}")

def main(args=None):
    rclpy.init(args=args)
    node = MyNode()
    rclpy.spin(node)
    rclpy.shutdown()

if __name__ == "__main__":
    main()
```

| [◀️ Prev: 04 ROS2 Node](../04_ros2_node/) | [🏠 Menu Utama](/) | [▶️ Next: 06 CPP Node](../06_cpp_node/) |
| ---------------------------------------- | ----------------- | -------------------------------------- |