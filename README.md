# MultiThreaded_Download_Manager
This is multi-threaded download manager written in modern C++ using lib-curl library

## Overview
Simple multi-threaded download manager example in modern C++ using libcurl and CMake.

## Requirements
- C++17 toolchain (gcc/clang/MSVC)
- CMake
- libcurl (development headers)

## Build — macOS
Install dependencies:
```bash
brew install cmake curl
```
Build:
```bash
cd /Users/aman/Downloads/MultiThread_Download_Manager-main
mkdir -p build && cd build
cmake ..
make -j$(sysctl -n hw.ncpu)
```

## Build — Linux (Debian/Ubuntu)
Install dependencies:
```bash
sudo apt update
sudo apt install build-essential cmake libcurl4-openssl-dev
```
Build:
```bash
cd /Users/aman/Downloads/MultiThread_Download_Manager-main
mkdir -p build && cd build
cmake ..
make -j$(nproc)
```

If CMake cannot find libcurl, provide hints:
```bash
cmake -DCURL_INCLUDE_DIR=/usr/include -DCURL_LIBRARY=/usr/lib/x86_64-linux-gnu ..
```

## Build — Windows
Recommended: use vcpkg to install libcurl and integrate with CMake.

Using vcpkg + Visual Studio:
1. Install vcpkg and curl:
```powershell
git clone https://github.com/microsoft/vcpkg.git
.\vcpkg\bootstrap-vcpkg.bat
.\vcpkg\vcpkg.exe install curl:x64-windows
.\vcpkg\vcpkg.exe integrate install
```
2. Configure and build with CMake (from Developer Command Prompt):
```powershell
cd C:\path\to\MultiThread_Download_Manager-main
mkdir build
cd build
cmake -G "Visual Studio 17 2022" -A x64 -DCMAKE_TOOLCHAIN_FILE=C:/path/to/vcpkg/scripts/buildsystems/vcpkg.cmake ..
cmake --build . --config Release
```
Binary will be in the appropriate Visual Studio output folder (e.g., Release).

Using MinGW (MSYS2):
1. Install MSYS2/mingw-w64 and libcurl (pacman).
2. From MINGW shell:
```bash
pacman -Syu mingw-w64-x86_64-toolchain mingw-w64-x86_64-cmake mingw-w64-x86_64-curl
cd /c/path/to/MultiThread_Download_Manager-main
mkdir -p build && cd build
cmake -G "MinGW Makefiles" ..
mingw32-make
```

If CMake can't find curl on Windows, set:
```powershell
cmake -DCURL_INCLUDE_DIR="C:/path/to/curl/include" -DCURL_LIBRARY="C:/path/to/curl/lib/libcurl.lib" ..
```

## Usage
Run the built executable and provide URLs (example):
```bash
./MultiThreaded_Download_Manager https://example.com/file1.zip https://example.com/file2.zip
```

## Troubleshooting
- Ensure libcurl dev files are installed for your platform.
- Use -DCURL_* variables to point CMake to curl headers/libs if auto-detection fails.
- For Windows, prefer vcpkg integration to simplify dependency discovery.

## License
Add a LICENSE file or choose a license before reusing this code in production.