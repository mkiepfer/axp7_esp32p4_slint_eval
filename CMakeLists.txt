# The following five lines of boilerplate have to be in your project's
# CMakeLists in this exact order for cmake to work correctly
cmake_minimum_required(VERSION 3.16)

include($ENV{IDF_PATH}/tools/cmake/project.cmake)
project(axp7_eval_slint)

set(Python_FIND_VIRTUALENV FIRST)
find_package(Python REQUIRED COMPONENTS Interpreter Development)
message(Python_EXECUTABLE: ${Python_EXECUTABLE})

add_custom_target(elf_size_analyze_${PROJECT_NAME}
    COMMAND ${Python_EXECUTABLE} -m elf_size_analyze -t arm-none-eabi- -w120 -HaFR ${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}.elf
    COMMENT "Evaluate size of binary"
)
