add_definitions(-DCRLE_VERBOSE)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -g")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O3")

if (${CMAKE_SYSTEM_NAME} MATCHES "AIX")
	add_definitions("-D_IBM_SOURCE")
	set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -maix64")
elseif (${CMAKE_SYSTEM_NAME} MATCHES "SunOS")
	add_definitions("-D_SUN_SOURCE")
	set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -m64")
elseif (${CMAKE_SYSTEM_NAME} MATCHES "Linux")
	add_definitions("-D_LINUX_SOURCE")
	set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -m64")
endif (${CMAKE_SYSTEM_NAME} MATCHES "AIX")

include_directories(${CMAKE_CURRENT_SOURCE_DIR})
include_directories(${PROJECT_SOURCE_DIR}/..)
add_executable(unittest unittest.c)
