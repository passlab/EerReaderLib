project(TestEerReader)

FIND_PACKAGE( OpenMP REQUIRED)
if(OPENMP_FOUND)
message("OPENMP FOUND")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${OpenMP_EXE_LINKER_FLAGS}")
endif()

set (CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

link_directories(${CMAKE_CURRENT_SOURCE_DIR}/../build/lib ${LIBTIFF_LIB_DIR})
set (PROJECT_LINK_LIBS EERReaderLib tiff)
include_directories(${LIBTIFF_INCLUDE_DIR}) 

# Target definition
add_executable(TestEerReader TestEerReader.cpp)
target_link_libraries(TestEerReader ${PROJECT_LINK_LIBS} )
