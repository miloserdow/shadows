cmake_minimum_required(VERSION 3.0)
project(shadows)

find_package(OpenCV)

file(GLOB shadows_lib_src
	"src/*.cpp"
	"src/utils/*.cpp"
)

include_directories(${CMAKE_SOURCE_DIR}/src)
include_directories(${OpenCV_INCLUDE_DIRS})
add_library(shadows_lib ${shadows_lib_src})
target_link_libraries(shadows_lib ${OpenCV_LIBS})

# Build demo application and copy samples if required by option
if(BUILD_EXAMPLES)
	set(sample_src
		main.cpp
	)
	add_executable(shadows_Demo ${sample_src})
	target_link_libraries(shadows_Demo shadows_lib)
	
	# Copy samples to build directory
	file(COPY yourDir DESTINATION yourDestination)
endif(BUILD_EXAMPLES)
