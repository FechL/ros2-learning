# Write a Python Service Server

Sekarang kita akan membuat **node service server** pertama Anda menggunakan **Python** di ROS2. Node ini akan menerima dua angka dari klien, lalu mengembalikan hasil penjumlahannya menggunakan **ROS2 Services**.

## 📁 Buat File Service Server

Arahkan ke folder:

```bash
ros2_ws/src/my_py_pkg/my_py_pkg/
```

Kemudian buat file Python baru, misalnya:

```bash
touch add_two_ints_server.py
chmod +x add_two_ints_server.py
```

## Isi Kode Node Service Server

```python
#!/usr/bin/env python3
import rclpy
from rclpy.node import Node
from example_interfaces.srv import AddTwoInts

class AddTwoIntsServerNode(Node):
    def __init__(self):
        super().__init__("add_two_ints_server")
        self.server = self.create_service(
            AddTwoInts,           # Tipe service
            "add_two_ints",       # Nama service
            self.callback_add_two_ints  # Callback saat request masuk
        )
        self.get_logger().info("Service 'add_two_ints' is ready to be called")
        
    def callback_add_two_ints(self, request: AddTwoInts.Request, response: AddTwoInts.Response):
        response.sum = request.a + request.b
        self.get_logger().info(f"{request.a} + {request.b} = {response.sum}")
        return response

def main(args=None):
    rclpy.init(args=args)
    node = AddTwoIntsServerNode()
    rclpy.spin(node)
    rclpy.shutdown()

if __name__ == "__main__":
    main()
```

Penjelasan Code

- Node dibuat dengan nama `"add_two_ints_server"`.
- Service didefinisikan menggunakan `example_interfaces/srv/AddTwoInts`.
- Nama service yang digunakan adalah `"add_two_ints"`.
- Fungsi `callback_add_two_ints()` akan dijalankan setiap kali ada request service masuk.
- Node akan menjumlahkan dua bilangan `a` dan `b` dari request, lalu mengembalikan hasilnya (`sum`) melalui response.

## Setup untuk Build

### Edit `setup.py`

Tambahkan ke bagian `entry_points`:

```python
'console_scripts': [
    "add_two_ints_server = my_py_pkg.add_two_ints_server:main"
]
```

### Edit `package.xml`

Tambahkan dependensi berikut jika belum:


```xml
<depend>example_interfaces</depend>
```

## Build dan Jalankan

Arahkan ke folder utama workspace:

```bash
cd ~/ros2_ws
colcon build --packages-select my_py_pkg
source install/setup.bash
```

Kemudian jalankan node:

```bash
ros2 run my_py_pkg add_two_ints_server
```

Jika berhasil, Anda akan melihat pesan seperti ini di terminal:

```
[INFO] [add_two_ints_server]: Service 'add_two_ints' is ready to be called
```

## Memanggil Service dari Terminal

Kita bisa memanggil service secara manual dengan perintah berikut:

```bash
ros2 service call /add_two_ints example_interfaces/srv/AddTwoInts "{a: 5, b: 7}"
```

Output terminal service server akan menunjukkan:

```
[INFO] [add_two_ints_server]: 5 + 7 = 12
```

---

| [◀️ Prev: 17 ROS2 Service](../17_ros2_service/) | [🏠 Menu Utama](/) | [▶️ Next: 19 Write a Python Client](../19_/) |
| ---------------------------------------------- | ----------------- | ------------------------------------------- |