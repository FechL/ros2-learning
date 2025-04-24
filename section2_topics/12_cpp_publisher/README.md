# Write a C++ Publisher

Sekarang kita akan membuat **node publisher** pertama Anda menggunakan **C++** di ROS2. Node ini akan mengirimkan pesan teks secara berkala ke sebuah topik bernama `/robot_news`.

## 📁 Buat File Publisher

Arahkan ke folder:

```bash
ros2_ws/src/my_cpp_pkg/src/
```

Kemudian buat file C++ baru, misalnya:

```bash
touch robot_news_station.cpp
```

## Isi Kode Node Publisher

```cpp
#include "rclcpp/rclcpp.hpp"
#include "example_interfaces/msg/string.hpp"

class RobotNewsStationNode : public rclcpp::Node
{
public:
    RobotNewsStationNode() : Node("robot_news_station"), robot_name_("R2D2")
    {
        publisher_ = this->create_publisher<example_interfaces::msg::String>("robot_news", 10);
        timer_ = this->create_wall_timer(std::chrono::milliseconds(500), std::bind(&RobotNewsStationNode::publishNews, this));
        RCLCPP_INFO(this->get_logger(), "Robot News Station has been started.");
    }

private:
    void publishNews()
    {
        auto msg = example_interfaces::msg::String();
        msg.data = std::string("Hi, this is ") + robot_name_ + std::string(" from the Robot News Station");
        publisher_->publish(msg);
    }

    std::string robot_name_;
    rclcpp::Publisher<example_interfaces::msg::String>::SharedPtr publisher_;
    rclcpp::TimerBase::SharedPtr timer_;
};

int main(int argc, char **argv)
{
    rclcpp::init(argc, argv);
    auto node = std::make_shared<RobotNewsStationNode>();
    rclcpp::spin(node);
    rclcpp::shutdown();
    return 0;
}
```

Penjelasan Code

- Node bernama `"robot_news_station"` dibuat menggunakan OOP.
- Publisher mengirim pesan bertipe `String` ke topik `robot_news`.
- Pesan dikirim setiap 500ms melalui `timer`.
- `robot_name_` adalah nama robot yang dimasukkan ke dalam pesan.

## Setup untuk Build

### Edit `CMakeLists.txt`

Tambahkan:

```cmake
find_package(example_interfaces REQUIRED)

add_executable(robot_news_station src/robot_news_station.cpp)
ament_target_dependencies(robot_news_station rclcpp example_interfaces)

install(TARGETS
  robot_news_station
  DESTINATION lib/${PROJECT_NAME}
)
```

### Edit `package.xml`

Tambahkan:

```xml
<depend>example_interfaces</depend>
```

## Build dan Run

Arahkan ke folder utama workspace:

```bash
cd ~/ros2_ws
colcon build --packages-select my_cpp_pkg
```

Jalankan node publisher:

```bash
ros2 run my_cpp_pkg robot_news_station
```

Contoh hasil terminal:

![terminal cpp publisher](/assets/terminal_cpp_publisher.png)

Jika node subscriber Python Anda masih berjalan (misalnya node `smartphone` dari sebelumnya), maka akan muncul pesan-pesan yang diterima oleh subscriber.

| [◀️ Prev: 11 Write a Python Subscriber](../11_python_subscriber/) | [🏠 Menu Utama](/) | [▶️ Next: 13 Write a C++ Subscriber](../13_cpp_subscriber/) |
| ---------------------------------------------------------------- | ----------------- | ---------------------------------------------------------- |