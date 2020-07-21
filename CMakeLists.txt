cmake_minimum_required(VERSION 3.11)
project(amalgamate)

set(CMAKE_CXX_STANDARD 17)

set(AMAL_LINUX 0)
set(AMAL_WINDOWS 0)
set(AMAL_APPLE 0)
set(AMAL_MSVC 0)
set(AMAL_MINGW 0)

if(UNIX AND NOT APPLE)
    set(AMAL_LINUX 1)
elseif(APPLE)
    #link_directories(/usr/local/opt/llvm/lib/)
    set(AMAL_APPLE 1)
elseif(WIN32)
    set(AMAL_WINDOWS 1)
    if(MSVC)
        set(AMAL_MSVC 1)
    elseif(MINGW)
        set(AMAL_MINGW 1)
    endif()
endif()

set(SOURCE_FILES Amalgamate.cpp juce_core_amalgam.cpp)


add_executable(amalgamate ${SOURCE_FILES})

if(AMAL_WINDOWS)

else()
    target_link_libraries(amalgamate pthread dl)
endif()