cmake_minimum_required(VERSION 3.22)
project(ps_test)

set(CMAKE_CXX_STANDARD 17)

include(FetchContent)

FetchContent_Declare(
        pocketsphinx
        GIT_REPOSITORY https://github.com/themariday/pocketsphinx.git
)

FetchContent_MakeAvailable(pocketsphinx)

target_include_directories(pocketsphinx PUBLIC ${pocketsphinx_SOURCE_DIR}/src)
target_include_directories(pocketsphinx PUBLIC ${pocketsphinx_SOURCE_DIR}/include)
target_include_directories(pocketsphinx PUBLIC ${pocketsphinx_BINARY_DIR})
target_include_directories(pocketsphinx PUBLIC ${pocketsphinx_BINARY_DIR}/include)
target_include_directories(pocketsphinx PRIVATE ${pocketsphinx_SOURCE_DIR}/src/util)

add_executable(ps_test main.cpp)
target_link_libraries(ps_test pocketsphinx)
