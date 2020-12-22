cmake_minimum_required(VERSION 3.10)

project(opengl_test VERSION 0.1)

find_package(OpenGL REQUIRED)

include_directories( ${OPENGL_INCLUDE_DIRS} )

find_package(GLEW REQUIRED)
if (GLEW_FOUND)
	include_directories( ${GLEW_INCLUDE_DIRS} )
	link_libraries( ${GLEW_LIBRARIES} )
endif()

if(CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
	add_compile_options(
		-g
		#-Wall -Wextra
		-fpermissive
	)
endif()


add_definitions(
	-DEXAMPLE
)


file(GLOB SRC_FILES
	*.cpp
)

add_executable(opengl_test
	${SRC_FILES}
)

target_link_libraries(opengl_test
	${OPENGL_LIBRARIES}
	glfw
)
