cmake_minimum_required(VERSION 3.11)

project(hello_triangle)

set(CMAKE_C_STANDARD 99)

set(GLFW_DIR "../../assets/glfw")
set(GLAD_DIR "../../assets/glad")
set(SOURCE_FILES
  ../../assets/glad/src/glad.c
  src/main.c
)

add_subdirectory(${GLFW_DIR})
add_subdirectory(${GLAD_DIR})

target_include_directories(hello_triangle_executable PUBLIC
  ${GLFW_DIR}/include
  ${GLAD_DIR}/include
)
target_link_libraries(hello_triangle_executable
  glfw
)
target_compile_definitions(hello_triangle_executable PRIVATE
  ROOT_PATH="${CMAKE_SOURCE_DIR}"
)

add_executable(hello_triangle_executable ${SOURCE_FILES})
