# Write a C++ Subscriber

Sekarang kita akan membuat **node subscriber** pertama Anda menggunakan **C++** di ROS2. Node ini akan mendengarkan pesan dari topik `/robot_news` yang sebelumnya dipublish oleh node `robot_news_station`.

## 📁 Buat File Subscriber

Arahkan ke folder:

```bash
ros2_ws/src/my_cpp_pkg/src/
```

Kemudian buat file C++ baru, misalnya:

```bash
touch smartphone.cpp
```

## Isi Kode Node Subscriber

```cpp
#include "rclcpp/rclcpp.hpp"
#include "example_interfaces/msg/string.hpp"

class SmartphoneNode : public rclcpp::Node
{
public:
    SmartphoneNode() : Node("smartphone")
    {
        subscriber_ = this->create_subscription<example_interfaces::msg::String>(
            "robot_news", 10,
            std::bind(&SmartphoneNode::callbackRobotNews, this, std::placeholders::_1)
        );
        RCLCPP_INFO(this->get_logger(), "Smartphone has been started.");
    }

private:
    void callbackRobotNews(const example_interfaces::msg::String::SharedPtr msg)
    {
        RCLCPP_INFO(this->get_logger(), "%s", msg->data.c_str());
    }

    rclcpp::Subscription<example_interfaces::msg::String>::SharedPtr subscriber_;
};

int main(int argc, char **argv)
{
    rclcpp::init(argc, argv);
    auto node = std::make_shared<SmartphoneNode>();
    rclcpp::spin(node);
    rclcpp::shutdown();
    return 0;
}
```

Penjelasan Code

- Node bernama `"smartphone"` dibuat menggunakan OOP.
- Subscriber dibuat untuk topik `robot_news` dengan jenis pesan `String`.
- Callback function akan menampilkan data yang diterima ke terminal.
- Jika node `robot_news_station` aktif, maka subscriber akan terus menerima pesan secara real-time.

## Setup untuk Build

### Edit `CMakeLists.txt`

Tambahkan:

```cmake
find_package(example_interfaces REQUIRED)

add_executable(smartphone src/smartphone.cpp)
ament_target_dependencies(smartphone rclcpp example_interfaces)

install(TARGETS
  smartphone
  DESTINATION lib/${PROJECT_NAME}
)
```

### Edit `package.xml`

Pastikan terdapat:

```xml
<depend>example_interfaces</depend>
```

## Build dan Run

Arahkan ke folder utama workspace:

```bash
cd ~/ros2_ws
colcon build --packages-select my_cpp_pkg
```

Jalankan node subscriber:

```bash
ros2 run my_cpp_pkg smartphone
```

Jika node publisher (`robot_news_station`) sedang aktif, maka output terminal akan menampilkan pesan seperti:

![terminal cpp subscriber](/assets/terminal_cpp_subscriber.png)
![rqt graph cpp](/assets/rqt_graph.png)

Node `smartphone` berhasil menerima dan menampilkan pesan dari node `robot_news_station`.

| [◀️ Prev: 12 Write a C++ Publisher](../12_cpp_publisher/) | [🏠 Menu Utama](/) | [▶️ Next: 14 Experiment on Topics with Turtlesim](../14_turtlesim_topics/) |
| -------------------------------------------------------- | ----------------- | ------------------------------------------------------------------------- |
