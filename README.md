# portaudio-examples

### Required Software ###

#### Apache Ant ####

1. Download and extract Apache Ant https://ant.apache.org.
    * Ensure that Apache Ant is in your PATH.
3. Install Apache Contrib (https://sourceforge.net/projects/ant-contrib/files/ant-contrib/1.0b3/ant-contrib-1.0b3-bin.zip/download)
    * Download, unzip and copy ant-contrib*.jar to your Apache Ant installation's lib directory.

#### CMake ####

1. Download and extract CMake https://cmake.org.
    * Ensure that CMake is in your PATH.

### PortAudio support

1. Download and unzip http://www.portaudio.com/download.html
2. `cd build && cmake .. && cmake --build .`
    * You'll end up with a dynamic and static library. E.g. libportaudio.dylib and libportaudio_static.a

## Build sample application

1. `ant`

## Run sample application

1. `TODO`
