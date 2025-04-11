#  Write a Node Using C++

## 📁 Struktur Folder

Arahkan ke direktori package Anda:

```bash
cd ~/ros2_ws/src/my_cpp_pkg/src
```

Buat file C++ node:

```bash
touch my_first_node.cpp
```

## Minimal C++ Node

Buka `my_first_node.cpp` dan isi dengan:

```cpp
#include "rclcpp/rclcpp.hpp"

int main(int argc, char **argv)
{
    rclcpp::init(argc, argv);
    auto node = std::make_shared<rclcpp::Node>("cpp_test");
    RCLCPP_INFO(node->get_logger(), "Hello CPP Node");
    rclcpp::spin(node);
    rclcpp::shutdown();
    return 0;
}
```

### Konfigurasi IntelliSense (Opsional)

Tekan `Ctrl+Shift+P` > **C/C++: Edit Configurations (JSON)**, lalu tambahkan `rclcpp` ke `includePath`:

```json
"includePath": [
    "${workspaceFolder}/**",
    "/opt/ros/humble/include/**"
],
```

### Instalasi Melalui `CMakeLists.txt`

Edit file `CMakeLists.txt` Anda seperti berikut:

```cmake
cmake_minimum_required(VERSION 3.8)
project(my_cpp_pkg)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)

add_executable(cpp_node src/my_first_node.cpp)
ament_target_dependencies(cpp_node rclcpp)

install(TARGETS
  cpp_node
  DESTINATION lib/${PROJECT_NAME}
)

ament_package()
```

### Build Project

Arahkan ke root workspace:

```bash
cd ~/ros2_ws
colcon build --packages-select my_cpp_pkg
```

### Menjalankan Node

```bash
source install/setup.bash
ros2 run my_cpp_pkg cpp_node
```

## Versi OOP (Class-based)

Gunakan pendekatan berbasis class untuk struktur yang lebih rapi dan scalable:

```cpp
#include "rclcpp/rclcpp.hpp"

class MyNode : public rclcpp::Node
{
public:
    MyNode() : Node("cpp_test"), counter_(0)
    {
        RCLCPP_INFO(this->get_logger(), "Hello CPP Node");
        timer_ = this->create_wall_timer(
            std::chrono::seconds(1),
            std::bind(&MyNode::timerCallBack, this));
    }

private:
    void timerCallBack()
    {
        counter_++;
        RCLCPP_INFO(this->get_logger(), "Hello %d", counter_);
    }

    rclcpp::TimerBase::SharedPtr timer_;
    int counter_;
};

int main(int argc, char **argv)
{
    rclcpp::init(argc, argv);
    auto node = std::make_shared<MyNode>();
    rclcpp::spin(node);
    rclcpp::shutdown();
    return 0;
}
```

| [◀️ Prev: 05 Python Node](../05_python_node/) | [🏠 Menu Utama](/) | [▶️ Next: 07 Template Node](../07_template_node/) |
| -------------------------------------------- | ----------------- | ------------------------------------------------ |