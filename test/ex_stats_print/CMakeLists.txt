cmake_minimum_required(VERSION 3.5 FATAL_ERROR)
project(ex_stats_print LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_BUILD_TYPE Debug)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_definitions(-D_GLIBCXX_USE_CXX11_ABI=1)

include_directories(.)
aux_source_directory(. MAIN_SRC)
add_executable(ex_stats_print ${MAIN_SRC})
  
find_package(PkgConfig REQUIRED)
pkg_check_modules (JEMALLOC jemalloc)
pkg_search_module(JEMALLOC REQUIRED jemalloc)
    
target_link_libraries(ex_stats_print
PRIVATE
  ${JEMALLOC_LIBRARIES}
)
 

