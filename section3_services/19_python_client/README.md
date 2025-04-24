# Write a Python Service Client

Sekarang kita akan membuat **node service client** pertama Anda menggunakan **Python** di ROS2. Node ini akan mengirim request ke server yang menerima dua angka, dan menerima hasil penjumlahannya.

## 📁 Buat File Service Client

Arahkan ke folder:

```bash
ros2_ws/src/my_py_pkg/my_py_pkg/
```

Kemudian buat file Python baru, misalnya:

```bash
touch add_two_ints_client.py
chmod +x add_two_ints_client.py
```

## Isi Kode Node Service Client

**Without OOP**

```python
#!/usr/bin/env python3
import rclpy 
from rclpy.node import Node
from example_interfaces.srv import AddTwoInts

def main(args=None):
    rclpy.init(args=args)
    node = Node("add_two_ints_client_no_oop")
    
    client = node.create_client(AddTwoInts, "add_two_ints")  # Membuat client untuk service "add_two_ints" dengan tipe AddTwoInts
    while not client.wait_for_service(timeout_sec=1.0):  # Tunggu hingga service tersedia
        node.get_logger().warn("Waiting for service to be available...")
        
    request = AddTwoInts.Request()  # Buat objek request
    request.a = 40
    request.b = 95 
    
    future = client.call_async(request)  # Kirim request secara asinkron ke server
    rclpy.spin_until_future_complete(node, future)  # Tunggu sampai hasilnya diterima
    
    response = future.result()  # Ambil hasil dari future
    node.get_logger().info(
        f"Result of add_two_ints: {request.a} + {request.b} = {response.sum}"
    )

    rclpy.shutdown() 

if __name__ == "__main__":
    main()

```

Penjelasan:

- Node dibuat dengan nama `"add_two_ints_client_no_oop"`.
- Membuat client untuk service `add_two_ints` dengan tipe `AddTwoInts`.
- Mengirim request `a = 40`, `b = 95` ke server.
- Menunggu response secara **sinkron** menggunakan `spin_until_future_complete`.
- Menampilkan hasil dari response di terminal.

**With OOP**

```python
#!/usr/bin/env python3
import rclpy
from rclpy.node import Node
from example_interfaces.srv import AddTwoInts
from functools import partial  # Untuk menyisipkan argumen tambahan di callback

class AddTwoIntsClient(Node):
    def __init__(self):
        super().__init__("add_two_ints_client")
        self.client = self.create_client(AddTwoInts, "add_two_ints")  # Buat client service
        
    def call_add_two_ints(self, a, b):  # Fungsi untuk mengirim request
        while not self.client.wait_for_service(timeout_sec=1.0):  # Tunggu hingga service aktif
            self.get_logger().warn("Waiting for service to be available...")
        
        request = AddTwoInts.Request()  # Buat request
        request.a = a
        request.b = b
        
        future = self.client.call_async(request)  # Kirim request secara async
        future.add_done_callback(partial(self.callback_call_add_two_ints, request=request))  
        # Setelah future selesai, jalankan callback sambil bawa data request
    
    def callback_call_add_two_ints(self, future, request):  # Callback saat response diterima
        response = future.result()
        self.get_logger().info(f"{request.a} + {request.b} = {response.sum}")

def main(args=None):
    rclpy.init(args=args)
    node = AddTwoIntsClient()  # Buat objek node
    node.call_add_two_ints(40, 95)
    node.call_add_two_ints(121, 68)
    node.call_add_two_ints(8, 77)
    rclpy.spin(node)
    rclpy.shutdown()

if __name__ == "__main__":
    main()
```

Penjelasan:

- Menggunakan kelas `AddTwoIntsClient` yang mewarisi `Node`.
- Dalam metode `call_add_two_ints()`, node membuat request lalu menunggu service tersedia.
- Request diproses **secara asinkron** dan callback ditambahkan menggunakan `future.add_done_callback()`.
- Callback `callback_call_add_two_ints()` dijalankan otomatis saat response diterima.
- Dengan desain ini, kita bisa **mengirim banyak request dalam satu node**.

## Setup untuk Build

### Edit `setup.py`

Tambahkan ke bagian `entry_points`:

```python
'console_scripts': [
    "add_two_ints_client = my_py_pkg.add_two_ints_client:main",
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
```

Sebelum jalankan node client, jalankan **node server** terlebih dahulu. Kemudian jalankan node:

```bash
ros2 run my_py_pkg add_two_ints_client
```

Jika berhasil, Anda akan melihat pesan seperti ini di terminal:
![terminal python client](/assets/terminal_python_client.png)

| [◀️ Prev: 18 Write a Python Server](../19_python_server/) | [🏠 Menu Utama](/) | [▶️ Next: 20 Write a CPP Server](../20_cpp_server/) |
| -------------------------------------------------------- | ----------------- | -------------------------------------------------- |