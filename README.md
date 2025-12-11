# Fullbright DLL for Minecraft Bedrock Edition

A minimal DLL that implements only the Fullbright feature for Minecraft Bedrock Edition (Windows).

## Features
- Fullbright (constant illumination, removes darkness)
- Toggle with F4 key
- Adjustable gamma value (default: 25.0)

## Building

### Requirements
- CMake 3.15+
- Visual Studio 2019/2022 (MSVC)
- Windows SDK

### Build Steps
```bash
mkdir build
cd build
cmake ..
cmake --build . --config Release
```

## Usage
1. Build the DLL
2. Inject `Fullbright.dll` into Minecraft Bedrock Edition
3. Press F4 to toggle Fullbright on/off

## Credits
Based on [flarialmc/dll-oss](https://github.com/flarialmc/dll-oss)

## License
MIT License