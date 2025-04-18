# Tutorial Instalasi ROS2 Humble

ROS2 Humble direkomendasikan karena masih aktif dikembangkan dengan dukungan hingga Mei 2027. Berikut adalah langkah-langkah instalasi ROS2 Humble di Ubuntu.

## Set Locale

Pastikan sistem Anda mendukung `UTF-8`. Untuk memeriksa dan mengatur locale:

```bash
locale  # periksa dukungan UTF-8

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verifikasi pengaturan
```

## Setup Source

Anda perlu menambahkan repository ROS2 apt pada sistem:

1. Pastikan Ubuntu Universe repository sudah diaktifkan:

```bash
sudo apt install software-properties-common
sudo add-apt-repository universe
```

2. Tambahkan kunci **ROS2 GPG** dengan apt:

```bash
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

3. Tambahkan repository ke source list:

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

## Install ROS2 Packages

Update repository apt dan install desktop:

```bash
sudo apt update
sudo apt upgrade
sudo apt install ros-humble-desktop
```

### Paket Tambahan (Opsional)

- **ROS-Base** (Bare Bones): Library komunikasi, paket pesan, command line tools tanpa GUI:

```bash
sudo apt install ros-humble-ros-base
```

- **Development tools**: Compiler dan tools lain untuk membangun paket ROS:

```bash
sudo apt install ros-dev-tools
```

## Setup Environment ROS2

Atur environment dengan mengikuti langkah-langkah berikut:

```bash
# Ganti ".bash" dengan shell yang Anda gunakan jika bukan bash
# Pilihan: setup.bash, setup.sh, setup.zsh
source /opt/ros/humble/setup.bash

# Buka file bashrc
gedit ~/.bashrc
```

Setelah file terbuka, tambahkan baris berikut di bagian akhir file dan simpan:

```
source /opt/ros/humble/setup.bash
```

## Uji Instalasi ROS2

Buka 2 terminal atau gunakan split terminal di terminator.

Pada terminal pertama (talker):

```bash
ros2 run demo_nodes_cpp talker  # bisa menggunakan cpp atau python
```

Pada terminal kedua (listener):

```bash
ros2 run demo_nodes_py listener  # bisa menggunakan python atau cpp
```

Jika berhasil, terminal talker akan menampilkan pesan `Publishing` dan listener akan menampilkan pesan `I heard`.

![terminal](/assets/terminal.png)

full dokumentasi klik [di sini](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html).

| [🏠 Menu Utama](/) | ▶️ [Next: Install Utility Tools](/utility/) |
| ----------------- | ------------------------------------------ |