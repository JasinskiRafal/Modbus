cmake_minimum_required(VERSION 3.13)
project(ModbusLibrary)

set(CMAKE_CXX_STANDARD 17)

if (DCMAKE_BUILD_TYPE MATCHES Debug)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -lpthread -Wall")
endif()

option(MODBUS_EXAMPLE "Build example program" ON)
option(MODBUS_TESTS "Build tests" ON)
option(MODBUS_COMMUNICATION "Use Modbus communication library" OFF)

add_subdirectory(src)

if(MODBUS_TESTS)
  add_subdirectory(tests)
endif()

if(MODBUS_EXAMPLE)
    add_executable(ex example/main.cpp)
    target_link_libraries(ex Modbus)
endif()

