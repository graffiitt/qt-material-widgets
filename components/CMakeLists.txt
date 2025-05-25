cmake_minimum_required(VERSION 3.20)

project(qt-material-components VERSION 2.0.0 LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Widgets)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Widgets)

set(LIB_TYPE "STATIC")

FILE(GLOB ORIGIN *.h *.cpp)
FILE(GLOB LIB lib/*.h lib/*.cpp)
FILE(GLOB LAYOUTS layouts/*.h layouts/*.cpp)

set(PROJECT_SOURCES
        ${ORIGIN}
        ${LIB}
        ${LAYOUTS}
        ${CMAKE_CURRENT_SOURCE_DIR}/resources.qrc
)

add_library(
        ${PROJECT_NAME} ${LIB_TYPE}
        ${PROJECT_SOURCES}
)

target_link_libraries(${PROJECT_NAME} PUBLIC
        Qt${QT_VERSION_MAJOR}::Widgets
)

target_include_directories(${PROJECT_NAME} PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/
)