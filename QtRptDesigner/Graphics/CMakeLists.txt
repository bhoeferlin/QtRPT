set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include_directories("${PROJECT_SOURCE_DIR}")
include_directories("${PROJECT_BINARY_DIR}")
include_directories("${PROJECT_SOURCE_DIR}/Graphics")

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Core Gui Xml PrintSupport Qml Widgets)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Core Gui Xml PrintSupport Qml Widgets)


add_library(Graphics_objs OBJECT
    GraphicsBox.cpp GraphicsBox.h
)
set_property(TARGET Graphics_objs
             PROPERTY POSITION_INDEPENDENT_CODE True)

#add_library(Graphics
#    $<TARGET_OBJECTS:Graphics_objs>
#)

target_link_libraries(Graphics_objs PRIVATE
    Qt${QT_VERSION_MAJOR}::Core
    Qt${QT_VERSION_MAJOR}::Gui
    Qt${QT_VERSION_MAJOR}::Xml
    Qt${QT_VERSION_MAJOR}::PrintSupport
    Qt${QT_VERSION_MAJOR}::Qml
    Qt${QT_VERSION_MAJOR}::Widgets
)

#target_include_directories(Graphics_objs PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
