# Build Tool Colcon

Agar dapat membuat dan mengelola program ROS 2, kamu membutuhkan sebuah build tool khusus bernama Colcon. ***Colcon*** merupakan penerus dari catkin dan ament, serta mendukung workspace dengan berbagai macam paket ROS 2 sekaligus.

## Instalasi Colcon
Untuk menginstal Colcon dan ekstensi umumnya, jalankan perintah berikut di terminal:
```bash
sudo apt install python3-colcon-commons-extensions
```
> Catatan: Paket colcon-common-extensions mencakup sekumpulan plugin penting untuk membangun dan menjalankan workspace ROS 2, seperti colcon-build, colcon-test, dan lainnya.

***Verifikasi Instalasi***
Untuk memastikan colcon sudah terinstal dengan benar, coba jalankan perintah:
```bash
colcon --help
```
Jika berhasil, kamu akan melihat daftar subcommands dan opsi konfigurasi dari colcon.

## Setup Auto-completion
Agar kamu bisa menggunakan fitur auto-completion saat menulis perintah colcon, kamu perlu menambahkan konfigurasi pada file ~/.bashrc.
setelah **.bashrc** dibuka, pada line terakhir copy tulis:

1. Buka file .bashrc dengan teks editor, misalnya:
    ```bash
    gedit ~/.bashrc
    ```
2. Scroll ke bagian paling bawah, lalu tambahkan baris berikut:
    ```bash
    source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash
    ```
3. Simpan file dan tutup editor, lalu jalankan:
    ```bash
    source ~/.bashrc
    ```

| [Menu Utama 🏠](/) | [Next ▶️ [02 create workspace]](../02_create_workspace/) |
|---|---|
|  |  |