cmake_minimum_required(VERSION 3.10)
project(solver)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CURRENT_SOURCE_DIR /home/ivan/MrShip15/workspace/projects/hw03)

add_library(solver_lib STATIC ${CMAKE_CURRENT_SOURCE_DIR}/solver_lib/solver.cpp)

include_directories(/solver_lib /formatter_lib /formatter_ex_lib)

add_executable(solver ${CMAKE_CURRENT_SOURCE_DIR}/solver_application/equation.cpp)

find_library(formatter NAMES libformatter.a PATHS ${CMAKE_CURRENT_SOURCE_DIR}/formatter_lib)
find_library(formatter_ex NAMES libformatter_ex.a PATHS ${CMAKE_CURRENT_SOURCE_DIR}/formatter_ex_lib)
find_library(solver_lib NAMES libsolver_lib.a PATHS ${CMAKE_CURRENT_SOURCE_DIR}/solver_lib)

target_link_libraries(solver ${formatter} ${formatter_ex} ${solver_lib})
