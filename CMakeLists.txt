project(h264_decoder)
cmake_minimum_required(VERSION 2.8)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/bin)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O3 -mavx -Wall")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O3 -Wall")

set(H264_DECODER_INCLUDE ${CMAKE_CURRENT_SOURCE_DIR}/src/inc)

add_library(meerkat_h264_decoder STATIC)

target_include_directories(meerkat_h264_decoder
		PUBLIC
		$<INSTALL_INTERFACE:inc>
		$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src/inc>
		)

add_subdirectory(src/src)

target_link_libraries(meerkat_h264_decoder)