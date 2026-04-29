cmake_minimum_required(VERSION 3.14)

project(QtXlsx VERSION 0.3.0 LANGUAGES CXX)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include_directories("${PROJECT_SOURCE_DIR}")
include_directories("${PROJECT_BINARY_DIR}")

find_package(Qt5 REQUIRED COMPONENTS Core Xml Gui)

set(TARGET_NAME qtxlsx)

set(SOURCES
    xlsxabstractooxmlfile.cpp
    xlsxabstractsheet.cpp
    xlsxcell.cpp
    xlsxcellformula.cpp
    #xlsxcelllocation.cpp
    xlsxchart.cpp
    xlsxcolor.cpp
    xlsxconditionalformatting.cpp
    xlsxcontenttypes.cpp
    xlsxdatavalidation.cpp
    xlsxdocument.cpp
    #xlsxdocument_p.cpp
    xlsxformat.cpp
    #xlsxformat_p.cpp
    xlsxmediafile.cpp
    xlsxnumformatparser.cpp
    xlsxrelationships.cpp
    xlsxrichstring.cpp
    xlsxsharedstrings.cpp
    xlsxstyles.cpp
    xlsxtheme.cpp
    #xlsxtitle.cpp
    #xlsxtooltip.cpp
    xlsxutility.cpp
    xlsxworkbook.cpp
    xlsxworksheet.cpp
)

set(HEADERS
    xlsxabstractooxmlfile.h
    xlsxabstractsheet.h
    xlsxcell.h
    xlsxcellformula.h
    #xlsxcelllocation.h
    xlsxchart.h
    #xlsxcolor.h
    xlsxconditionalformatting.h
    #xlsxcontenttypes.h
    xlsxdatavalidation.h
    xlsxdocument.h
    xlsxformat.h
    #xlsxmediafile.h
    #xlsxnumformatparser.h
    #xlsxrelationships.h
    xlsxrichstring.h
    #xlsxsharedstrings.h
    #xlsxstyles.h
    #xlsxtheme.h
    #xlsxtitle.h
    #xlsxtooltip.h
    #xlsxutility.h
    xlsxworkbook.h
    xlsxworksheet.h
)

add_library(QtXlsx_objs OBJECT
    ${SOURCES}
    ${HEADERS}
)

add_library(QtXlsx
    $<TARGET_OBJECTS:QtXlsx_objs>
)

#add_library(QtXlsx_shared SHARED
#    $<TARGET_OBJECTS:QtXlsx_objs>
#)

target_link_libraries(QtXlsx_objs PRIVATE
    Qt5::Core
    Qt5::Xml
    Qt5::Gui
    Qt5::GuiPrivate
)
target_link_libraries(QtXlsx PRIVATE
    Qt5::Core
    Qt5::Xml
    Qt5::Gui
    Qt5::GuiPrivate
)

#target_link_libraries(QtXlsx_shared PRIVATE
#    Qt5::Core
#    Qt5::Xml
#    Qt5::Gui
#    Qt5::GuiPrivate
#)
#set_target_properties(QtXlsx_shared PROPERTIES OUTPUT_NAME QtXlsx)

