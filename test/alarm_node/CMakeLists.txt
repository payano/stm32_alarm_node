file(GLOB SRCS *.cpp)

ADD_EXECUTABLE(nodeTests ${SRCS})

TARGET_LINK_LIBRARIES(nodeTests
	libgtest
	libgmock
)


include_directories(
)

add_test(NAME nodeTests
         COMMAND nodeTests)

