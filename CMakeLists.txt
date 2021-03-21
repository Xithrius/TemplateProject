cmake_minimum_required(VERSION 3.17)

project("TemplateProject")
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add our main executable
file(GLOB MY_SOURCES "src/*.cpp" "src/*.hpp" "src/*.h" "include/TemplateProject/*.h" "include/TemplateProject/*.hpp")
add_executable("${PROJECT_NAME}" ${MY_SOURCES})

# Add our library and make its headers available
add_library("${PROJECT_NAME}_utilities" "utilities/src/lib.cpp" "utilities/include/utilities/lib.hpp")
target_include_directories("${PROJECT_NAME}_utilities"
        PUBLIC
        "utilities/include"
        PRIVATE
        "include/utilities/include"
        )

target_link_libraries("${PROJECT_NAME}"
        PRIVATE
        "${PROJECT_NAME}_utilities"
)
