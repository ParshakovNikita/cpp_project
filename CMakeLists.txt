cmake_minimum_required(VERSION 3.14)

project(cpp_project)

include_directories(include)

add_executable(main main.cpp src/my_add.cpp)

# Использование FetchContent для загрузки GoogleTest
include(FetchContent)
FetchContent_Declare(
    googletest
    GIT_REPOSITORY https://github.com/google/googletest.git
    GIT_TAG v1.15.2
)

FetchContent_MakeAvailable(googletest)

enable_testing()

add_executable(tests test_add.cpp src/my_add.cpp)

target_link_libraries(tests gtest gtest_main)

include(GoogleTest)
gtest_discover_tests(tests)

set(BUILD_SHARED_LIBS OFF)  # Это сделает линковку статической
