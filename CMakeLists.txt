project(zieds)
cmake_minimum_required(VERSION 3.1.0)

set(CMAKE_C_FLAGS "-Wall -Wpedantic -Wextra -Wshadow -Wno-conversoin -Wno-sign-conversion -std=c99")

set(SRC_LIST "src/bloom_filter.c"
	     "src/hashes.c")
set(INCLUDE_LIST "include/bloom_filter.h"
                 "src/hashes.h")

include_directories("include/")

add_library(zieds SHARED ${SRC_LIST}
			 ${INCLUDE_LIST})

add_executable(example "src/example.c"
			${INCLUDE_LIST})
target_link_libraries(example zieds)
