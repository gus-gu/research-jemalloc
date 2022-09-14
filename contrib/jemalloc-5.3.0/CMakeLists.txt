# cmake最低版本号要求
cmake_minimum_required(VERSION 3.10)
# 指定的项目名
project(jemalloc)
set(CMAKE_EXPORT_COMPILECOMMANDS ON)
# 添加头文件目录
include_directories(include)
include_directories(test/include)

aux_source_directory(include/jemalloc/internal INCLUDE_INTERNAL_SRC)
aux_source_directory(src MAIN_SRC)
aux_source_directory(test/analyze TEST_ANALYZE_SRC)
aux_source_directory(test/include/test TEST_INCLUDE_SRC)
aux_source_directory(test/integration TEST_INTEGRATION_SRC)
aux_source_directory(test/src TEST_SRC_SRC)
aux_source_directory(test/stress TEST_STRESS_SRC)
aux_source_directory(test/stress TEST_UNIT_SRC)
#指定生成的可执行文件，第一个参数为文件名
add_library(${PROJECT_NAME} 
${INCLUDE_INTERNAL_SRC}
${MAIN_SRC}
${TEST_ANALYZE_SRC}
${TEST_INCLUDE_SRC}
${TEST_INTEGRATION_SRC}
${TEST_SRC_SRC}
${TEST_STRESS_SRC}
${TEST_UNIT_SRC})
