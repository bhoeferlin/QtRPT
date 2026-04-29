set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Core Gui Xml PrintSupport Sql Widgets)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Core Gui Xml PrintSupport Sql Widgets)

add_library(SQLDiagram_objs OBJECT
    diagramdocument.cpp diagramdocument.h
    #Barcode.cpp Barcode.h
    #numbertoarabicword.cpp numbertoarabicword.h
)
set_property(TARGET SQLDiagram_objs
             PROPERTY POSITION_INDEPENDENT_CODE True)

add_library(SQLDiagram
    $<TARGET_OBJECTS:SQLDiagram_objs>
)

target_link_libraries(Graphics_objs PRIVATE
    Qt${QT_VERSION_MAJOR}::Core
    Qt${QT_VERSION_MAJOR}::Gui
    Qt${QT_VERSION_MAJOR}::PrintSupport
    Qt${QT_VERSION_MAJOR}::Sql
    Qt${QT_VERSION_MAJOR}::Qml
    Qt${QT_VERSION_MAJOR}::Widgets
)
