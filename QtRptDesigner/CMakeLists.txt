cmake_minimum_required(VERSION 3.16.0)

project(QtRptDesigner VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if(CMAKE_VERSION VERSION_LESS "3.7.0")
    set(CMAKE_INCLUDE_CURRENT_DIR ON)
endif()


include_directories("${PROJECT_SOURCE_DIR}")
include_directories("${PROJECT_BINARY_DIR}")
include_directories("${PROJECT_SOURCE_DIR}/../QtRPT")
include_directories("${PROJECT_SOURCE_DIR}/Graphics")
#include_directories("${PROJECT_SOURCE_DIR}/SQLDiagram")

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Core Gui Xml PrintSupport Sql Qml Charts Widgets)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Core Gui Xml PrintSupport Sql Qml Charts Widgets)
add_subdirectory("${PROJECT_SOURCE_DIR}/Graphics")
add_executable(QtRptDesigner
    $<TARGET_OBJECTS:QtRPT_objs>
    $<TARGET_OBJECTS:Graphics_objs>
    mainwindow.ui
    PageSettingDlg.ui
    ReportBand.ui
    EditFldDlg.ui
    FldPropertyDlg.ui
    RepScrollArea.ui
    SettingDlg.ui
    SqlDesigner.ui
    ScriptEditor.ui

    mainwindow.h
    PageSettingDlg.h
    ReportBand.h
    EditFldDlg.h
    aboutDlg.h
    FldPropertyDlg.h
    RepScrollArea.h
    SettingDlg.h
    SqlDesigner.h
    XmlViewModel.h
    CustomInterface.h
    ScriptEditor.h

    mainwindow.cpp
    PageSettingDlg.cpp
    ReportBand.cpp
    EditFldDlg.cpp
    aboutDlg.cpp
    FldPropertyDlg.cpp
    RepScrollArea.cpp
    SettingDlg.cpp
    SqlDesigner.cpp
    XmlViewModel.cpp
    ScriptEditor.cpp
    main.cpp
)

target_link_libraries(QtRptDesigner PRIVATE
    QtRPT
    Qt${QT_VERSION_MAJOR}::Core
    Qt${QT_VERSION_MAJOR}::Gui
    Qt${QT_VERSION_MAJOR}::Xml
    Qt${QT_VERSION_MAJOR}::PrintSupport
    Qt${QT_VERSION_MAJOR}::Sql
    Qt${QT_VERSION_MAJOR}::Qml
    Qt${QT_VERSION_MAJOR}::Charts
    Qt${QT_VERSION_MAJOR}::Widgets
    Graphics_objs
)

#set(EXAMPLE_FILES
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example.sqlite
    #${PROJECT_SOURCE_DIR}/examples/examples_report/qt_background_portrait.png
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example1.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example2.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example3.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example4.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example5.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example6a.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example6b.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example7a.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example7b.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example8.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example9.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example10.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example11.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example12.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example13.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example15.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example16.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example17.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example18.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example19.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example20.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example21.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/example22.xml
    #${PROJECT_SOURCE_DIR}/examples/examples_report/RussianInvaders.xml
#)

#add_custom_target(copy_files ALL
    #DEPENDS QtRptDemo
    #COMMAND ${CMAKE_COMMAND} -E make_directory ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/examples_report
    #COMMAND ${CMAKE_COMMAND} -E copy_if_different
    #${EXAMPLE_FILES}
    #${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/examples_report
#)
