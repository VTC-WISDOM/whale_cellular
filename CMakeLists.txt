cmake_minimum_required(VERSION 3.13)

set(target "whale_cellular_module")
project(${target} C CXX ASM)

add_subdirectory(./libs/rp2x_sim7080g)

add_library(${target} INTERFACE)

target_sources(${target} INTERFACE
	src/whale_cellular.c
)

target_include_directories(${target} INTERFACE
	..
)

target_link_libraries(${target} INTERFACE
	rp2x_sim7080g_lib
)

target_compile_definitions(${target} INTERFACE
	W_CELL_UART=uart0
	W_CELL_TX=0
	W_CELL_RX=1

)

