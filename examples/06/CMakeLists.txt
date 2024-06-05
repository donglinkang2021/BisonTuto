cmake_minimum_required(VERSION 3.16)
project(simple_c)

set(SRC_DIR "src")
set(PARSER_DIR ${CMAKE_CURRENT_BINARY_DIR})

## Flex/Bison configuration 
find_package(BISON REQUIRED)
find_package(FLEX REQUIRED)

set(LEXER_OUT ${PARSER_DIR}/lexer.c)
set(PARSER_OUT ${PARSER_DIR}/parser.c)

flex_target(LEXER ${SRC_DIR}/lexer.l ${LEXER_OUT} DEFINES_FILE ${PARSER_DIR}/lexer.h)
bison_target(PARSER ${SRC_DIR}/parser.y ${PARSER_OUT} DEFINES_FILE ${PARSER_DIR}/parser.h)
add_flex_bison_dependency(LEXER PARSER)

add_executable(
    calc
    ${SRC_DIR}/main.c
    ${LEXER_OUT}
    ${PARSER_OUT}
)
target_include_directories(calc PRIVATE "${PARSER_DIR}")