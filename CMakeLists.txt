cmake_minimum_required(VERSION 3.20)

project(Ember
    VERSION 0.1.0
    LANGUAGES CXX
)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# ----------------------------------------
# Output directories
# ----------------------------------------

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY
    ${CMAKE_BINARY_DIR}../..//bin
)

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY
    ${CMAKE_BINARY_DIR}/lib
)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY
    ${CMAKE_BINARY_DIR}/lib
)

# ----------------------------------------
# Engine library
# ----------------------------------------

add_library(Engine
    src/engine/Engine.cpp
)

target_include_directories(Engine
    PUBLIC
        src
)

# ----------------------------------------
# Engine application
# ----------------------------------------

add_executable(Ember
    src/main.cpp
)

target_link_libraries(Ember
    PRIVATE
        Engine
)

# ----------------------------------------
# Tests
# ----------------------------------------

enable_testing()
add_subdirectory(tests)

