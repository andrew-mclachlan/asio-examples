# Quick start guide to building with CMake.
#
# Download, install and add CMake to you PATH ( https://cmake.org/download ).
#
# For Windows, do:
#   cd build
#   cmake .. -G "Visual Studio 10 2010" (for VS2010)
#     or
#   cmake .. -G "Visual Studio 14 2015" (for VS2015)
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

if(APPLE)

include_directories(${COMMON_INCLUDES} /Users/amclach/Work/trunky/A2B/portaudio/include)

target_link_libraries(${PROJECT_NAME} /Users/amclach/Work/trunky/A2B/portaudio/build/libportaudio.dylib)

else()

include_directories(${COMMON_INCLUDES} /home/amclach/GitHub/portaudio/include)

target_link_libraries(${PROJECT_NAME} /home/amclach/GitHub/portaudio/build/libportaudio.so)

endif()

set_target_properties(${PROJECT_NAME} PROPERTIES OUTPUT_NAME "portaudio-examples")

target_compile_definitions(${PROJECT_NAME} PUBLIC
                            UNIX)

set_target_properties(${PROJECT_NAME} PROPERTIES COMPILE_FLAGS "-Werror")
    
set(CMAKE_CXX_FLAGS "-std=c++11")
