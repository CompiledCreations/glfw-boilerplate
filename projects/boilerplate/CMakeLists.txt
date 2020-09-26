add_executable(boilerplate src/main.cpp)

target_link_libraries(boilerplate glfw glad)
target_include_directories(boilerplate PRIVATE ${LINMATH_INCLUDE_DIR})
