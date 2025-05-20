# Template Node

Berikut adalah **template lengkap node OOP** baik untuk Python maupun C++ di ROS2. Template ini bisa dijadikan dasar setiap kali Anda membuat node baru, cukup ganti bagian-bagian yang ditandai dengan **MODIFY NAME** agar sesuai dengan fungsi dan nama node yang Anda inginkan.

## OOP Python Node Template

```python
#!/usr/bin/env python3
import rclpy
from rclpy.node import Node

class MyCustomNode(Node):  # 🔧 MODIFY NAME: Nama class node
    def __init__(self):
        super().__init__("node_name")  # 🔧 MODIFY NAME: Nama node yang dikenali oleh ROS2

def main(args=None):
    rclpy.init(args=args)
    node = MyCustomNode()  # 🔧 MODIFY NAME: Instance dari class node
    rclpy.spin(node)
    rclpy.shutdown()

if __name__ == "__main__":
    main()
```

📝 *Catatan:*
- Gunakan `create_timer`, `create_publisher`, `create_subscription`, dll. di dalam `__init__()` untuk menambahkan fungsionalitas node.
- Nama node di `super().__init__()` harus unik dalam sistem ROS.

## OOP C++ Node Template

```cpp
#include "rclcpp/rclcpp.hpp"

class MyCustomNode : public rclcpp::Node // 🔧 MODIFY NAME: Nama class
{
public:
    MyCustomNode() : Node("node_name") // 🔧 MODIFY NAME: Nama node yang dikenali oleh ROS2
    {
        // Tambahkan publisher, subscriber, timer, dll di sini
    }

private:
    // Tambahkan variabel/member function di sini
};

int main(int argc, char **argv)
{
    rclcpp::init(argc, argv);
    auto node = std::make_shared<MyCustomNode>(); // 🔧 MODIFY NAME: Instance dari class node
    rclcpp::spin(node);
    rclcpp::shutdown();
    return 0;
}
```

📝 *Catatan:*
- Gunakan `create_wall_timer`, `create_publisher`, `create_subscription`, dll. di dalam constructor untuk menambahkan fitur node.

Kedua template ini cocok dijadikan **boilerplate** awal dalam pengembangan sistem ROS2 berbasis OOP.

| [◀️ Prev: 06 CPP Node](../06_cpp_node/) | [🏠 Menu Utama](/) | [▶️ Next: 08 Section 1 Conclusion](../08_section1_conclusion/) |
| -------------------------------------- | ----------------- | ------------------------------------------------------------- |