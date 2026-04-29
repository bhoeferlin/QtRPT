cmake_minimum_required(VERSION 3.16.0)

project(XYZ VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include_directories("${PROJECT_SOURCE_DIR}")
include_directories("${PROJECT_BINARY_DIR}")

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Core Gui Xml PrintSupport Sql Qml Widgets)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Core Gui Xml PrintSupport Sql Qml Widgets)

add_library(XYZ_COMMON OBJECT
    Barcode.cpp Barcode.h
    CommonClasses.cpp CommonClasses.h
    numbertoarabicword.cpp numbertoarabicword.h
)
set_property(TARGET XYZ_COMMON
             PROPERTY POSITION_INDEPENDENT_CODE True)

target_link_libraries(XYZ_COMMON PRIVATE
    Qt${QT_VERSION_MAJOR}::Core
    Qt${QT_VERSION_MAJOR}::Gui
    Qt${QT_VERSION_MAJOR}::Xml
    Qt${QT_VERSION_MAJOR}::Widgets
)

#------------------------------------

add_library(XYZ_UI OBJECT
    chart.cpp chart.h
    keyFilter.cpp keyFilter.h
    SQLHighlighter.cpp SQLHighlighter.h
    tableDelegates.cpp tableDelegates.h
    tableWidgetHTML.cpp tableWidgetHTML.h
    XYZ_Container.cpp XYZ_Container.h
    XYZ_ColorSelector.cpp XYZ_ColorSelector.h
    XYZ_DownloadManager.cpp XYZ_DownloadManager.h
    XYZ_Label.cpp XYZ_Label.h
    XYZ_Logger.cpp XYZ_Logger.h
    XYZ_ParamTree.cpp XYZ_ParamTree.h
    XYZ_TextEdit.cpp XYZ_TextEdit.h
    XYZ_TextEditor.cpp XYZ_TextEditor.h XYZ_TextEditor.ui
    XYZ_UpdateDlg.cpp XYZ_UpdateDlg.h XYZ_UpdateDlg.ui
)
set_property(TARGET XYZ_UI
             PROPERTY POSITION_INDEPENDENT_CODE True)

target_link_libraries(XYZ_UI PRIVATE
    Qt${QT_VERSION_MAJOR}::Core
    Qt${QT_VERSION_MAJOR}::Gui
    Qt${QT_VERSION_MAJOR}::Xml
    Qt${QT_VERSION_MAJOR}::PrintSupport
    Qt${QT_VERSION_MAJOR}::Sql
    Qt${QT_VERSION_MAJOR}::Qml
    Qt${QT_VERSION_MAJOR}::Widgets
)
