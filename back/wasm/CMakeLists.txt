cmake_minimum_required(VERSION 3.0)

project(NeuroWebAssembly)

set(CMAKE_C_COMPILER "emcc")
set(CMAKE_CXX_COMPILER "em++")

add_executable(main mainWasm.cpp)

set(CMAKE_CXX_FLAGS "--target=wasm32-unknown-emscripten")

target_include_directories(main include)