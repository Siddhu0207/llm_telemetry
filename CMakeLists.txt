cmake_minimum_required(VERSION 3.14)
project(llm_telemetry LANGUAGES CXX)

# Force the compiler to use modern C++17 on ALL platforms
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Define your source files generically
add_executable(telemetry_run 
    src/main.cpp 
)

# Cross-platform dependency linking (FTXUI and llama.cpp)
target_link_libraries(telemetry_run PRIVATE ftxui::screen ftxui::dom ftxui::component)