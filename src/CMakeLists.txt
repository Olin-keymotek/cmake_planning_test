# 中间层CMakeLists.txt进行撰写。

# 中间层的代码是planing_main.cpp，以它为目标完成可执行文件的生成和链接头文件和库。

project(planing_main)

# 下一层的子目录
add_subdirectory(pnc_map)
add_subdirectory(process)

# 可执行文件
add_executable(${PROJECT_NAME} planing_main.cpp)

# 包含头文件
target_include_directories(${PROJECT_NAME}
PUBLIC
${Process_Dir}
)
# CMAKE_SOURCE_DIR 指的就是整个项目的根目录。
# 在父类定义的变量，子类可以直接调用。

# 链接这个动态库
target_link_libraries(${PROJECT_NAME}
PUBLIC
process
)
