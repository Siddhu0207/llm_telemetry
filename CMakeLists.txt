cmake_minimum_required(VERSION 3.24)
project(LLM_Telemetry C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 1. Bring in the Llama engine 
set(LLAMA_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(LLAMA_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
add_subdirectory(third_party/llama.cpp)

# 2. Bring in the UI Framework
set(FTXUI_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
set(FTXUI_BUILD_DOCS OFF CACHE BOOL "" FORCE)
add_subdirectory(third_party/ftxui)

# 3. Define our main telemetry executable
add_executable(telemetry_run src/main.cpp)

# 4. CRITICAL FIX: Tell the compiler exactly where the header files are located
target_include_directories(telemetry_run PRIVATE 
    ${CMAKE_CURRENT_SOURCE_DIR}/third_party/llama.cpp/include
    ${CMAKE_CURRENT_SOURCE_DIR}/third_party/llama.cpp/ggml/include
)

# 5. Link everything together safely
target_link_libraries(telemetry_run 
    PRIVATE 
    llama           
    ftxui::screen   
    ftxui::dom      
    ftxui::component 
)