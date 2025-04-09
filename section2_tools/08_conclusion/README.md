## 01
Colcon adalah fondasi penting dalam proses build dan manajemen workspace ROS 2. Pastikan instalasi dan setup sudah benar sebelum lanjut ke tahap selanjutnya.

## 02
Workspace adalah fondasi pengembangan ROS 2. Pastikan workspace telah dibuat, di-source, dan siap untuk digunakan sebelum menambahkan package atau coding.

## 03
- Gunakan ros2 pkg create untuk membuat package dengan Python atau C++
- Edit package.xml dan CMakeLists.txt sesuai kebutuhan
- Build menggunakan colcon build
- Jangan lupa source setelah build agar package dikenali oleh terminal

# 04
- Node adalah blok utama dari sistem ROS 2.
- Mereka bekerja secara modular dan dapat berkomunikasi lintas bahasa.
- Desain node yang baik akan membuat aplikasi robotik lebih skalabel, handal, dan terorganisir.