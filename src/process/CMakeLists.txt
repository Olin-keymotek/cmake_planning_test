project(process)

# 动态链接库
add_library(${PROJECT_NAME} 
SHARED
process.cpp
)

# 包含头文件 
target_include_directories(${PROJECT_NAME}
PUBLIC
${PNC_Map_Dir}
)

# 链接pnc_map这个库
target_link_libraries(${PROJECT_NAME}
PUBLIC
pnc_map
)