cmake_minimum_required(VERSION 3.13)
project(matplotcpp)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXE_LINKER_FLAGS "-Xlinker -export-dynamic")
#set(ENV{PYTHON_EXECUTABLE} /usr/bin/python2)

set(PYTHON_INCLUDE_DIRS /usr/include/python2.7)
set(PYTHON_LIBRARIES /usr/lib/python2.7/config-x86_64-linux-gnu/libpython2.7.so)

# include_directories(ext/plot/ /opt/share/.pyenv/versions/3.7.3/include/python3.7m)
# link_directories(/opt/share/.pyenv/versions/3.7.3/lib/python3.7/config-3.7m-x86_64-linux-gnu /opt/share/.pyenv/versions/3.7.3/lib)

#find_package(PythonLibs 2.7 REQUIRED)
include_directories(${PYTHON_INCLUDE_DIRS})
message("the pythonlibs:" ${PYTHON_INCLUDE_DIRS})

add_executable(matplotcpp main.cpp matplotlibcpp.h)

target_link_libraries(matplotcpp pthread crypt dl util m opencv_core opencv_imgproc ${PYTHON_LIBRARIES})


