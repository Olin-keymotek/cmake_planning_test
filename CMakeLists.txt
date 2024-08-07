# 先从顶层的CMakeLists.txt进行写

cmake_minimum_required(VERSION 3.29.0)

#工程名可以写详细写
project(planing
    VERSION 0.0.3
    DESCRIPTION "a demo of cmake planning"
    HOMEPAGE_URL "https://github.com/Olin-keymotek/cmake_planning_test"
    LANGUAGES CXX
)

set(CMAKE_CXX_STANDARD 17)

# 变量设置，设置的变量会传递到这个子目录中去。
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
set(Process_Dir ${CMAKE_SOURCE_DIR}/src/process)
set(PNC_Map_Dir ${CMAKE_SOURCE_DIR}/src/pnc_map)

# CMakeLists.txt顶层目录下没有任何的代码，就直接添加其子目录。
# 添加子目录--找这个srb子目录中的CMakeLists.txt
add_subdirectory(src)



