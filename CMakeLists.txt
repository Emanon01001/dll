cmake_minimum_required(VERSION 3.15)
project(Fullbright VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Windows specific settings
if(WIN32)
    add_definitions(-DUNICODE -D_UNICODE -DWIN32_LEAN_AND_MEAN)
endif()

# MinHook library
add_library(minhook STATIC
    lib/minhook/src/buffer.c
    lib/minhook/src/hook.c
    lib/minhook/src/trampoline.c
    lib/minhook/src/hde/hde32.c
    lib/minhook/src/hde/hde64.c
)
target_include_directories(minhook PUBLIC lib/minhook/include)

# Main DLL
add_library(Fullbright SHARED
    src/main.cpp
    src/Memory/Memory.cpp
    src/Memory/SignatureScanner.cpp
    src/Hook/Hook.cpp
    src/Hook/GetGammaHook.cpp
    src/Fullbright/Fullbright.cpp
)

target_include_directories(Fullbright PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/src
    ${CMAKE_CURRENT_SOURCE_DIR}/lib/minhook/include
)

target_link_libraries(Fullbright PRIVATE minhook)

# Output settings
set_target_properties(Fullbright PROPERTIES
    OUTPUT_NAME "Fullbright"
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin"
)