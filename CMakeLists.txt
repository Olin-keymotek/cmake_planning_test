cmake_minimum_required(VERSION 3.29.0)

project(planning)

Set(CMAKE_CXX_STANDARD 17)

# 在Windows环境下，.exe为可执行文件 .dll为动态库

# set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
# 【可执行文件，需要在运行的时候加载动态库，所以动态库需要放在可执行文件的同一目录。】
# 01 设置可执行文件存放路径  -- 使用该宏定义，windwos环境下动态库和exe文件制定在在bin目录下
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)
# CMAKE_LIBRARY_OUTPUT_DIRECTORY--Lniux平台下用。动态库和exe文件制定在在bin目录下
# CMAKE_ARCHIVE_OUTPUT_DIRECTORY--静态库，这个只会把库得路径指定下来。可执行文件不管。


# 02 动态库生成 - src中的.cpp文件生成一个动态库
aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LISTS)
add_library(common
SHARED
${SRC_LISTS}
)
# 动态库依赖头文件，所以需要包含头文件的目录。
target_include_directories(common
PUBLIC
${PROJECT_SOURCE_DIR}/include
)

# 03 可执行文件
# planing_main生成可执行文件
add_executable(planing_main planing_main.cpp)
# 同样需要包含头文件
target_include_directories(planing_main
PUBLIC
${PROJECT_SOURCE_DIR}/include
)

# 04 可执行文件需要链接生成的动态库
target_link_libraries(planing_main
PUBLIC
common
)