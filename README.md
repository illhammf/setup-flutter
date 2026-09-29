# Flutter Mobile Development Setup Journey

## Complete Flutter Environment Setup Documentation

Dokumentasi ini berisi proses setup Flutter Mobile Development untuk mata kuliah Pemrograman Mobile 2026.

Setup dibuat oleh:

**Ilham Firmansyah**

Tujuan:
- Membuat environment Flutter.
- Menggunakan WSL2 sebagai development environment.
- Menghubungkan Flutter dengan Android device fisik.
- Membuat dan menjalankan project Flutter pertama.

---

# 1. Development Environment

## Laptop

```
Owner:
Ilham Firmansyah

OS:
Windows

Processor:
AMD Ryzen 3

Environment:
WSL2 Ubuntu

Editor:
Visual Studio Code
```

Laptop digunakan untuk:
- Menjalankan Windows.
- Menjalankan WSL2.
- Coding Flutter.
- Build aplikasi Android.

---

## Android Device

```
Owner:
Ilham Firmansyah

Device:
POCO X3 NFC

Model:
M2007J20CG

Android:
Android 12

API:
31
```

Digunakan sebagai:
- Device testing Flutter.
- Pengganti Android Emulator.
- Media debugging.

---

# 2. Architecture

```
Windows Laptop
      |
      |
     WSL2
      |
      |
Flutter SDK + Android SDK
      |
      |
 USB Connection
      |
      |
POCO X3 NFC
```

---

# 3. WSL2 Setup

Cek WSL melalui Windows PowerShell:

```powershell
wsl -l -v
```

Pastikan:

```
Ubuntu VERSION 2
```

---

# 4. Windows PowerShell dan Ubuntu WSL

## PowerShell digunakan untuk:

- Instalasi usbipd.
- Menghubungkan USB device.
- Konfigurasi Windows.

Contoh:

```powershell
usbipd list
```

## Ubuntu WSL digunakan untuk:

- Flutter.
- Dart.
- Android SDK.
- Git.

Contoh:

```bash
flutter doctor
```

---

# 5. User Development

Awalnya WSL menggunakan root.

Cek:

```bash
whoami
```

Disarankan menggunakan user biasa agar:

- Permission aman.
- Git tidak bermasalah.
- Project mudah dikelola.

Cek user:

```bash
cat /etc/passwd | grep /home
```

Masuk user:

```bash
su - ilhamfirmansyah
```

---

# 6. Folder Structure

Folder utama:

```
/home/ilhamfirmansyah/perkuliahan/pemrograman_mobile
```

Struktur:

```
pemrograman_mobile

├── flutter
├── Android
└── project_flutter
```

---

# 7. Java Setup

Flutter Android membutuhkan Java.

Versi:

```
OpenJDK 17
```

Cek:

```bash
java -version
javac -version
```

Set:

```bash
export JAVA_HOME="/usr/lib/jvm/java-17-openjdk-amd64"
```

Tambahkan permanen:

```bash
echo 'export JAVA_HOME="/usr/lib/jvm/java-17-openjdk-amd64"' >> ~/.zshrc
```

---

# 8. Flutter Installation

Install dependency:

```bash
sudo apt install -y curl git unzip xz-utils zip libglu1-mesa
```

Download Flutter:

```bash
cd ~/perkuliahan/pemrograman_mobile

git clone https://github.com/flutter/flutter.git -b stable --depth 1
```

Lokasi:

```
/home/ilhamfirmansyah/perkuliahan/pemrograman_mobile/flutter
```

Tambahkan environment:

```bash
export FLUTTER_HOME="/home/ilhamfirmansyah/perkuliahan/pemrograman_mobile/flutter"

export PATH="$FLUTTER_HOME/bin:$PATH"
```

Cek:

```bash
flutter --version
```

---

# 9. Android SDK

Android SDK digunakan untuk build aplikasi Android.

Lokasi:

```
/home/ilhamfirmansyah/perkuliahan/pemrograman_mobile/Android
```

Environment:

```bash
export ANDROID_HOME="/home/ilhamfirmansyah/perkuliahan/pemrograman_mobile/Android"

export PATH="$ANDROID_HOME/platform-tools:$PATH"
```

---

# 10. Flutter Doctor

Jalankan:

```bash
flutter doctor -v
```

Target:

```
[✓] Flutter

[✓] Android toolchain

[✓] Connected device
```

---

# 11. VS Code WSL

Install extension:

- WSL
- Remote Development
- Flutter
- Dart

Buka project dari WSL:

```bash
code .
```

Pastikan VS Code menunjukkan:

```
WSL: Ubuntu
```

---

# 12. Membuat Project Flutter

Masuk folder:

```bash
cd ~/perkuliahan/pemrograman_mobile
```

Buat project:

```bash
flutter create hello_world
```

Masuk:

```bash
cd hello_world
```

---

# 13. Connect Android Device

Aktifkan pada POCO X3 NFC:

- Developer Options.
- USB Debugging.
- File Transfer Mode.

---

# 14. Install USBIPD

Dilakukan melalui Windows PowerShell:

```powershell
winget install --interactive --exact dorssel.usbipd-win
```

---

# 15. Hubungkan HP ke WSL

Cek:

```powershell
usbipd list
```

Contoh:

```
BUSID 1-3 POCO X3 NFC
```

Share:

```powershell
usbipd bind --busid 1-3
```

Attach:

```powershell
usbipd attach --wsl --busid 1-3
```

BUSID setiap komputer dapat berbeda.

---

# 16. Cek ADB

Pada WSL:

```bash
adb devices
```

Jika berhasil:

```
b9c129d0 device
```

---

# 17. Flutter Device

Cek:

```bash
flutter devices
```

Output:

```
M2007J20CG (mobile)
Android 12
```

---

# 18. Run Flutter

Masuk project:

```bash
cd ~/perkuliahan/pemrograman_mobile/hello_world
```

Jalankan:

```bash
flutter run
```

---

# 19. Flutter Run Command

Saat aplikasi berjalan:

| Command | Fungsi |
|-|-|
| r | Hot Reload |
| R | Hot Restart |
| q | Stop aplikasi |
| d | Detach |

---

# 20. Git Workflow

Inisialisasi:

```bash
git init
```

Tambah:

```bash
git add .
```

Commit:

```bash
git commit -m "message"
```

Push:

```bash
git push
```

---

# 21. Daily Workflow

Setiap mulai coding:

## Windows PowerShell

Hubungkan HP:

```powershell
usbipd attach --wsl --busid 1-3
```

## WSL

Masuk user:

```bash
su - ilhamfirmansyah
```

Masuk project:

```bash
cd ~/perkuliahan/pemrograman_mobile/nama_project
```

Run:

```bash
flutter run
```

---

# Final Status

```
✓ WSL2 Ubuntu

✓ Java JDK 17

✓ Flutter SDK

✓ Android SDK

✓ VS Code WSL

✓ GitHub

✓ POCO X3 NFC Connected

✓ Flutter App Running
```

Environment siap digunakan untuk pembelajaran Flutter Mobile Development.
