cmake_minimum_required(VERSION 3.20)

project(qt-material-example VERSION 0.1 LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Widgets)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Widgets)

FILE(GLOB ORIGIN *.cpp *.h *.ui)

set(PROJECT_SOURCES
        ${ORIGIN}
        ${CMAKE_CURRENT_SOURCE_DIR}/examples.qrc
)

add_executable(${PROJECT_NAME}
        ${PROJECT_SOURCES}
)

target_link_libraries(${PROJECT_NAME} PRIVATE
        Qt${QT_VERSION_MAJOR}::Widgets
        qt-material-components
)

target_include_directories(${PROJECT_NAME} PUBLIC
    components
)
