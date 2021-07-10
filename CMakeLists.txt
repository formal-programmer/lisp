cmake_minimum_required(VERSION 3.10)
project(lisp)

################################################################################
## SETTINGS
################################################################################

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

################################################################################
## TARGETS
################################################################################

set(LISP_CSTD_LIB       cstd)
set(LISP_EXTERN_LIBS    ${LISP_CSTD_LIB})

set(LISP_SYNTAX_LIB     lisp-syntax)
set(LISP_LIBS           ${LISP_SYNTAX_LIB})

set(LISP_COMPILER_BIN   lispc)
set(LISP_BINS           ${LISP_COMPILER_BIN})

foreach(lib ${LISP_EXTERN_LIBS})
    add_subdirectory(lib/${lib})
endforeach()

foreach(lib ${LISP_LIBS})
    add_subdirectory(${lib})
endforeach()

foreach(bin ${LISP_BINS})
    add_subdirectory(${bin})
endforeach()