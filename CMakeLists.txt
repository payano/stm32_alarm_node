cmake_minimum_required(VERSION 3.10)

set(CMAKE_CXX_FLAGS "-Wall -std=c++0x -pedantic -O2 -Werror -Wextra -fexceptions")

if(UNIX)
	add_definitions(-DUNIX) 
endif (UNIX)

if(APPLE)
	add_definitions(-DUNIX) 
	add_definitions(-DGTEST_USE_OWN_TR1_TUPLE=1)
	set(CMAKE_CXX_FLAGS "-std=c++11 -stdlib=libc++ -U__STRICT_ANSI__")
endif (APPLE)

project(hello_library)
find_package (Threads REQUIRED)

add_subdirectory(test)


############################################################
# Create an executable
############################################################

# Add an executable with the above sources
add_executable(hello_binary 
    main.c
)

target_link_libraries (hello_binary 
${CMAKE_THREAD_LIBS_INIT}
)

include_directories(cmake-build-debug/test/gtest/src/gtest/googletest/include)
