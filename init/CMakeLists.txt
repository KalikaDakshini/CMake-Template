cmake_minimum_required(VERSION 4.2)
project("CPP Project" LANGUAGES CXX)

# Set variables
set(MAIN_TARGET "project")
set(BIN_DIR "./bin")
set(TST_DIR "./tests")

# Main executable
add_executable(${MAIN_TARGET} src/main.cpp)

# Compilation flags
set(BASE_FLAGS
	-Wall -Wextra -Wshadow -Wnon-virtual-dtor
	-Wold-style-cast -Wcast-align -Woverloaded-virtual
	-pedantic -Werror
)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
target_compile_options(${MAIN_TARGET} PRIVATE ${BASE_FLAGS})

# Build specific options
target_compile_options(${MAIN_TARGET} PRIVATE
	$<$<CONFIG:Release>:-O3>
)
target_compile_options(${MAIN_TARGET} PRIVATE
	$<$<CONFIG:Debug>:-ggdb -fsanitize=address -O0>
)
target_link_options(${MAIN_TARGET} PRIVATE
	$<$<CONFIG:Debug>:-fsanitize=address>
)

# Executable name
if(CMAKE_BUILD_TYPE STREQUAL "Debug")
	set_target_properties(${MAIN_TARGET} PROPERTIES
		OUTPUT_NAME "tranny.dbg"
		RUNTIME_OUTPUT_DIRECTORY "${BIN_DIR}"
	)
else()
	set_target_properties(${MAIN_TARGET} PROPERTIES
		OUTPUT_NAME "tranny.app"
		RUNTIME_OUTPUT_DIRECTORY "${BIN_DIR}"
	)
endif()

# Link libraries
