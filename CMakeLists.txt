cmake_minimum_required(VERSION 3.10)
project(homework_1_task_2 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Output paths
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/results/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/results/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/results/bin)

# Add include folder
include_directories(${PROJECT_SOURCE_DIR}/include)

# Library
add_library(ipb_arithmetic
    src/sum.cpp
    src/subtract.cpp
)

# Example executable
add_executable(example_output src/main.cpp)
target_link_libraries(example_output ipb_arithmetic)

# Install targets
install(TARGETS ipb_arithmetic example_output
    RUNTIME DESTINATION bin
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
)

# Install headers
install(DIRECTORY include/ DESTINATION include)
