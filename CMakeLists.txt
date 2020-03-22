cmake_minimum_required(VERSION 3.11)
project(amalgamate)

set(CMAKE_CXX_STANDARD 17)

set(SOURCE_FILES Amalgamate.cpp juce_core_amalgam.cpp)

add_executable(amalgamate ${SOURCE_FILES})
target_link_libraries(amalgamate pthread dl)
