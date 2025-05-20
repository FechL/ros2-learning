# Write a C++ Service Server

Sekarang kita akan membuat **node service server** menggunakan **C++** di ROS 2. Node ini akan menangani permintaan penjumlahan dua bilangan bulat dari client.

## 📁 Buat File Server

Arahkan ke folder:

```bash
ros2_ws/src/my_cpp_pkg/src/
```

Kemudian buat file C++ baru, misalnya:

```bash
touch add_two_ints_server.cpp
```

## Isi Kode Node Server

```cpp
#include "example_interfaces/srv/add_two_ints.hpp"
#include "rclcpp/rclcpp.hpp"

using namespace std::placeholders; // Untuk bind placeholder fungsi callback

class AddTwoIntsServerNode : public rclcpp::Node {
  public:
    AddTwoIntsServerNode() : Node("add_two_ints_server") {
        server_ = this->create_service<
            example_interfaces::srv::AddTwoInts>( // Buat service server
            "add_two_ints",                       // Nama servicenya
            std::bind(&AddTwoIntsServerNode::callbackAddTwoInts, this, _1,
                      _2) // Binding callback
        );
        RCLCPP_INFO(this->get_logger(),
                    "Add Two Ints Service has been started.");
    }

  private:
    void callbackAddTwoInts(
        const example_interfaces::srv::AddTwoInts::Request::SharedPtr
            request, // Data request dari client
        const example_interfaces::srv::AddTwoInts::Response::SharedPtr
            response // Tempat menaruh hasil (sum)
    ) {
        response->sum = request->a + request->b;
        RCLCPP_INFO(this->get_logger(), "%d + %d = %d", (int)request->a,
                    (int)request->b, (int)response->sum);
    }

    rclcpp::Service<example_interfaces::srv::AddTwoInts>::SharedPtr
        server_; // Deklarasi service server
};

int main(int argc, char **argv) {
    rclcpp::init(argc, argv);
    auto node = std::make_shared<AddTwoIntsServerNode>(); // Buat objek node
    rclcpp::spin(node);
    rclcpp::shutdown();
    return 0;
}
```

## Penjelasan Code

- `create_service<...>` digunakan untuk membuat service server.
- `callbackAddTwoInts()` akan dipanggil setiap kali client mengirim request.
- `response->sum = request->a + request->b` adalah proses utama server.
- Node akan terus berjalan hingga ditutup secara manual (Ctrl+C).

## Setup untuk Build

### Edit `CMakeLists.txt`

Tambahkan baris berikut:

```cmake
add_executable(add_two_ints_server src/add_two_ints_server.cpp)
ament_target_dependencies(add_two_ints_server rclcpp example_interfaces)

install(TARGETS
  add_two_ints_server
  DESTINATION lib/${PROJECT_NAME}
)
```

### Edit `package.xml`

Tambahkan dependensi berikut jika belum ada:

```xml
<depend>example_interfaces</depend>
```

## Build dan Run

Arahkan ke folder utama workspace:

```bash
cd ~/ros2_ws
colcon build --packages-select my_cpp_pkg
```

Kemudian jalankan node:

```bash
ros2 run my_cpp_pkg add_two_ints_server
```

Contoh hasil terminal dengan client python:
![terminal cpp server](/assets/terminal_cpp_server.png)

| [◀️ Prev: 19 Write a Python Client](../19_python_client/) | [🏠 Menu Utama](/) | [▶️ Next: 21 Write a CPP Client](../21_cpp_client/) |
| -------------------------------------------------------- | ----------------- | -------------------------------------------------- |