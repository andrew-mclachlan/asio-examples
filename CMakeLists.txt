# Quick start guide to building with CMake.
#
# Download, install and add CMake to you PATH ( https://cmake.org/download ).
#
# For Windows, do:
#   cd build
#   cmake .. -G "Visual Studio 14 2015" (for VS2015)
#     or
#   cmake .. -G "Visual Studio 15 2017" (for VS2017)
#   cmake --build . --config Release
#
# For Unix, do:
#   cd build
#   cmake .. -DCMAKE_BUILD_TYPE=Release
#   cmake --build .

cmake_minimum_required (VERSION 3.5)
project(portaudio-examples)

set(SOURCES 
    ../src/main.cxx)

set(HEADERS
    ../inc/main.h)

set(COMMON_INCLUDES
    ../inc)

add_executable(${PROJECT_NAME} ${SOURCES} ${HEADERS})

include_directories(${COMMON_INCLUDES} ${PORTAUDIO_HOME}/include)

if(MSVC)

    # add macros and disable security warnings for stl code and multi byte for MFC
    add_definitions(-D_CRT_SECURE_NO_WARNINGS -D__SCL_SECURE_NO_WARNINGS -DNO_WARN_MBCS_MFC_DEPRECATION)

    # treat warnings as errors
    set_target_properties(${PROJECT_NAME} PROPERTIES COMPILE_FLAGS "/WX")

    target_link_libraries(${PROJECT_NAME} ${PORTAUDIO_HOME}/build/Release/portaudio_x86.lib)

else()

    if(APPLE)

    target_link_libraries(${PROJECT_NAME} ${PORTAUDIO_HOME}/build/libportaudio.dylib)

    else()

    target_link_libraries(${PROJECT_NAME} ${PORTAUDIO_HOME}/build/libportaudio.so)

    endif()

    set_target_properties(${PROJECT_NAME} PROPERTIES OUTPUT_NAME "portaudio-examples")

    target_compile_definitions(${PROJECT_NAME} PUBLIC
                                UNIX)

    set_target_properties(${PROJECT_NAME} PROPERTIES COMPILE_FLAGS "-Werror")
        
    set(CMAKE_CXX_FLAGS "-std=c++11")

endif()
