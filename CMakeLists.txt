cmake_minimum_required(VERSION 3.16)  # use a stable version

project(BudgetTracker)

set(CMAKE_CXX_STANDARD 20)

include(FetchContent)
FetchContent_Declare(
        Catch2
        GIT_REPOSITORY https://github.com/catchorg/Catch2.git
        GIT_TAG v3.5.3
)
FetchContent_MakeAvailable(Catch2)

# Main executable
add_executable(BudgetTracker main.cpp)

# Test executable — NOTE: remove 'cmake-build-debug' paths!
add_executable(tests tests/test.cpp tests/test.h)

# Link Catch2 to test target
target_link_libraries(tests PRIVATE Catch2::Catch2WithMain)

include(CTest)
include(Catch)
catch_discover_tests(tests)
