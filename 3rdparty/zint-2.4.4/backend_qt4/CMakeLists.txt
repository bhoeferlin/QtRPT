cmake_minimum_required(VERSION 3.1.0)

project(qzint VERSION 0.1 LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt5 COMPONENTS Widgets Core Gui Xml Qml Sql PrintSupport Charts REQUIRED)
find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Core)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Core)

#include(${CMAKE_CURRENT_LIST_DIR}/../CommonFiles/CMakeLists.txt)
#include(${CMAKE_CURRENT_LIST_DIR}/../3rdparty/zint-2.4.4/backend_qt4/CMakeLists.txt)

#include_directories(${CMAKE_CURRENT_SOURCE_DIR})
#file (GLOB SOURCES *.h *.cpp)
#0file (GLOB QtRPT_SOURCES RELATIVE "Dir_QtRPT" *.h *.cpp)
set(QZINT_SOURCES
    ${CMAKE_CURRENT_LIST_DIR}/qzint.h
    ${CMAKE_CURRENT_LIST_DIR}/qzint_global.h
    ${CMAKE_CURRENT_LIST_DIR}/qtrptnamespace.h
    ${CMAKE_CURRENT_LIST_DIR}/RptSql.h
    ${CMAKE_CURRENT_LIST_DIR}/RptFieldObject.h
    ${CMAKE_CURRENT_LIST_DIR}/RptBandObject.h
    ${CMAKE_CURRENT_LIST_DIR}/RptPageObject.h
    ${CMAKE_CURRENT_LIST_DIR}/RptCrossTabObject.h
    ${CMAKE_CURRENT_LIST_DIR}/RptScriptEngine.h
    ${CMAKE_CURRENT_LIST_DIR}/RptDsInline.h
    ${CMAKE_CURRENT_LIST_DIR}/RptDsAbstract.h

    ${CMAKE_CURRENT_LIST_DIR}/qzint.cpp
    ${CMAKE_CURRENT_LIST_DIR}/RptDsPlugin.cpp
    ${CMAKE_CURRENT_LIST_DIR}/RptSql.cpp
    ${CMAKE_CURRENT_LIST_DIR}/RptFieldObject.cpp
    ${CMAKE_CURRENT_LIST_DIR}/RptBandObject.cpp
    ${CMAKE_CURRENT_LIST_DIR}/RptPageObject.cpp
    ${CMAKE_CURRENT_LIST_DIR}/RptCrossTabObject.cpp
    ${CMAKE_CURRENT_LIST_DIR}/RptScriptEngine.cpp
    ${CMAKE_CURRENT_LIST_DIR}/RptDsInline.cpp
    ${CMAKE_CURRENT_LIST_DIR}/RptDsAbstract.cpp
)

#add_definitions(-DNO_BARCODE)

include_directories(${CMAKE_CURRENT_LIST_DIR})

add_library(qzint SHARED ${QZINT_SOURCES})

target_link_libraries(qzint PRIVATE  Qt5::Core Qt5::Widgets Qt5::Xml Qt5::PrintSupport Qt5::Charts Qt5::Sql Qt5::Qml)
