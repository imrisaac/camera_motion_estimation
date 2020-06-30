cmake_minimum_required(VERSION 3.0.0)

project(CameraMotion)
set(TARGET camMotion)

set(CMAKE_CXX_FLAGS "${CMKE_CXX_FLAGS} -std=c++11")

find_package(OpenCV 3.4.1 REQUIRED)
find_package(PkgConfig REQUIRED)
find_package (Eigen3 3.3 REQUIRED)

include_directories(${OpenCV_INCLUDE_DIRS}
                    ${CMAKE_BINARY_DIR} # this is the build dir, where the generated version.h file is located
                    ${EIGEN3_INCLUDE_DIR}
                    ${PROJECT_SOURCE_DIR}/src        
                    )       

file(GLOB_RECURSE SOURCES "src/*.cpp")

add_executable(${TARGET} ${SOURCES})

target_link_libraries(${TARGET}
                      ${OpenCV_LIBS}
                      )

