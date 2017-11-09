CMAKE_MINIMUM_REQUIRED(VERSION 3.1)

# If a C++11 compiler is available, then set the appropriate flags
  set(CMAKE_CXX_STANDARD 11)
  set(CMAKE_CXX_STANDARD_REQUIRED ON)
  set(CMAKE_CXX_EXTENSIONS OFF)

project(myapp C CXX)

set(CMAKE_BUILD_TYPE "Release")

find_package(OpenMVG REQUIRED)
include_directories(${OPENMVG_INCLUDE_DIRS})
set(LIBS ${LIBS} ${OPENMVG_LIBRARIES})

find_package(Eigen3 3.3.4 REQUIRED)
include_directories(${EIGEN3_INCLUDE_DIRS})
#SET( EIGEN3_INCLUDE_DIR "$ENV{EIGEN3_INCLUDE_DIR}" )
#IF( NOT EIGEN3_INCLUDE_DIR )
#    MESSAGE( FATAL_ERROR "Please point the environment variable EIGEN3_INCLUDE_DIR to the include directory of your Eigen3 installation.")
#ENDIF()
#INCLUDE_DIRECTORIES ( "${EIGEN3_INCLUDE_DIR}" )

#Bring the headers, such as Student.h into the project
include_directories(include)
 
#Can manually add the sources using the set command as follows:
#set(SOURCES src/mainapp.cpp src/Student.cpp)
 
#However, the file(GLOB...) allows for wildcard additions:
file(GLOB SOURCES "src/*.cpp")
 
add_executable(helloworld ${SOURCES})
target_link_libraries(helloworld ${OPENMVG_LIBRARIES})
