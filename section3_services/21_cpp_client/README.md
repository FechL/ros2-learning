Berikut adalah dokumentasi **ROS 2 C++ Service Client** dengan dua versi: tanpa OOP dan dengan OOP, lengkap dengan penjelasan per baris seperti dokumentasi sebelumnya.

# Write a C++ Service Client

Sekarang kita akan membuat **node service client** menggunakan **C++** di ROS2. Node ini akan mengirim request ke server untuk menjumlahkan dua bilangan.

## 📁 Buat File Service Client

Arahkan ke folder:

```bash
ros2_ws/src/my_cpp_pkg/src/
```

Kemudian buat file baru, misalnya:

```bash
touch add_two_ints_client.cpp
```

## Isi Kode Node Client

**Tanpa OOP**

```cpp
#include "example_interfaces/srv/add_two_ints.hpp"
#include "rclcpp/rclcpp.hpp"

using namespace std::chrono_literals; // Untuk literal waktu seperti 1s

int main(int argc, char **argv) {
    rclcpp::init(argc, argv);
    auto node = std::make_shared<rclcpp::Node>(
        "add_two_ints_client_no_oop"); // Buat node biasa (tanpa class)

    auto client = node->create_client<example_interfaces::srv::AddTwoInts>(
        "add_two_ints"); // Buat client untuk service "add_two_ints"

    while (!client->wait_for_service(1s)) // Tunggu sampai service tersedia
    {
        RCLCPP_WARN(node->get_logger(), "Waiting for the server...");
    }

    auto request =
        std::make_shared<example_interfaces::srv::AddTwoInts::Request>();
    request->a = 6;
    request->b = 2;

    auto future =
        client->async_send_request(request); // Kirim request secara async
    rclcpp::spin_until_future_complete(
        node, future); // Tunggu hingga respons diterima

    auto response = future.get(); // Ambil hasil dari server
    RCLCPP_INFO(node->get_logger(), "%d + %d = %d", (int)request->a,
                (int)request->b, (int)response->sum);

    rclcpp::shutdown();
    return 0;
}
```

Penjelasan:

- Node `add_two_ints_client_no_oop` dibuat tanpa class.
- Request dikirim ke server dan ditunggu menggunakan `spin_until_future_complete`.
- Hasil dijumlah dan ditampilkan ke terminal.

**Dengan OOP**

```cpp
#include "example_interfaces/srv/add_two_ints.hpp"
#include "rclcpp/rclcpp.hpp"

using namespace std::chrono_literals; // Untuk literal waktu 1s
using namespace std::placeholders;    // Untuk bind placeholder (_1)

class AddTwoIntsClientNode : public rclcpp::Node {
  public:
    AddTwoIntsClientNode() : Node("add_two_ints_client") {
        client_ = this->create_client<example_interfaces::srv::AddTwoInts>(
            "add_two_ints"); // Buat client untuk service
    }

    void callAddTwoInts(int a, int b) // Fungsi untuk kirim request
    {
        while (!client_->wait_for_service(1s)) // Tunggu service aktif
        {
            RCLCPP_WARN(this->get_logger(), "Waiting for the server...");
        }

        auto request =
            std::make_shared<example_interfaces::srv::AddTwoInts::Request>();
        request->a = a;
        request->b = b;

        client_->async_send_request(
            request,
            std::bind(&AddTwoIntsClientNode::callbackCallAddTwoInts, this, _1));
        // Kirim request dan pasang callback jika respons diterima
    }

  private:
    void callbackCallAddTwoInts(
        rclcpp::Client<example_interfaces::srv::AddTwoInts>::SharedFuture
            future) {
        auto response = future.get(); // Ambil response
        RCLCPP_INFO(this->get_logger(), "Sum: %d", (int)response->sum);
    }

    rclcpp::Client<example_interfaces::srv::AddTwoInts>::SharedPtr
        client_; // Deklarasi client
};

int main(int argc, char **argv) {
    rclcpp::init(argc, argv);
    auto node = std::make_shared<AddTwoIntsClientNode>(); // Buat objek node

    node->callAddTwoInts(10, 5);
    node->callAddTwoInts(12, 7);
    node->callAddTwoInts(1, 2);

    rclcpp::spin(node);
    rclcpp::shutdown();
    return 0;
}
```

### Penjelasan

- Node dibungkus dalam class `AddTwoIntsClientNode`.
- Method `callAddTwoInts()` digunakan untuk mengirim request dan menangani respons.
- Cocok untuk penggunaan **berulang** atau **dinamis**, karena bisa kirim request berkali-kali.

## Setup untuk Build

### Edit `CMakeLists.txt`

Tambahkan:

```cmake
add_executable(add_two_ints_client src/add_two_ints_client.cpp)
ament_target_dependencies(add_two_ints_client rclcpp example_interfaces)

install(TARGETS
  add_two_ints_client
  DESTINATION lib/${PROJECT_NAME}
)
```

### Edit `package.xml`

Tambahkan jika belum:

```xml
<depend>example_interfaces</depend>
```

## Build dan Jalankan

Arahkan ke folder utama workspace:

```bash
cd ~/ros2_ws
colcon build --packages-select my_cpp_pkg
```

Jalankan node **server** terlebih dahulu, kemudian jalankan client:

```bash
ros2 run my_cpp_pkg add_two_ints_client
```

Contoh hasil terminal:
![terminal cpp client](/assets/terminal_cpp_client.png)

| [◀️ Prev: 20 Write a CPP Server](../20_cpp_server/) | [🏠 Menu Utama](/) | [▶️ Next: 22 Experiment on Services with Turtlesim](../21_turtlesim_service/) |
| -------------------------------------------------- | ----------------- | ---------------------------------------------------------------------------- |