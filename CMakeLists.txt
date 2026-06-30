cmake_minimum_required(VERSION 3.14)
project(llm_telemetry LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

 
set(LLAMA_BUILD_TESTS OFF CACHE INTERNAL "")
set(LLAMA_BUILD_EXAMPLES OFF CACHE INTERNAL "")

 
add_subdirectory(third_party/ftxui)
add_subdirectory(third_party/llama.cpp)

 
add_executable(telemetry_run 
    src/main.cpp 
)
 
target_include_directories(telemetry_run PRIVATE 
    third_party/llama.cpp
    third_party/llama.cpp/include
)

 
target_link_libraries(telemetry_run PRIVATE 
    ftxui::screen 
    ftxui::dom 
    ftxui::component
    llama
)