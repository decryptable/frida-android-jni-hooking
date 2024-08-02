# Android Native Hooking Project

This project demonstrates how to perform native hooking on Android applications using Frida. It includes scripts for intercepting and logging JNI function calls within native libraries.

## Project Structure

- `info.js`: A Frida script to log all loaded native libraries and their JNI functions.
- `hook.js`: A Frida script to hook specific JNI functions in a specified native library.
- `list_all_loaded.js`: A Frida script to list all loaded native libraries and their functions.

## Getting Started

### Prerequisites

- [Frida](https://frida.re) must be installed on your system.
- You need root access on your Android device or emulator.
- Ensure you have [adb](https://developer.android.com/studio/command-line/adb) installed and properly configured.

### Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/yourusername/android-native-hooking.git
    cd android-native-hooking
    ```

2. Connect your Android device or start your emulator.

3. Forward the necessary ports for Frida:
    ```sh
    adb forward tcp:27042 tcp:27042
    adb forward tcp:27043 tcp:27043
    ```

4. Start the Frida server on your Android device:
    ```sh
    adb shell "/data/local/tmp/frida-server &"
    ```

### Usage

#### Info Script

The `info.js` script logs all loaded native libraries and their JNI functions:

```sh
frida -U -f com.example.targetapp -l info.js --no-pause

