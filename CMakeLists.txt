
cmake_minimum_required(VERSION 3.21)

project(NexusGui VERSION 0.1 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt6 6.12 REQUIRED COMPONENTS
    Quick
    Quick3D
)

qt_standard_project_setup(REQUIRES 6.5)

qt_add_executable(NexusGui
    src/main.cpp
)

qt_add_qml_module(NexusGui
    URI Nexus.Gui
    VERSION 1.0

    SOURCES
"${CMAKE_CURRENT_LIST_DIR}/src/Visuals/HoloCoreGeometry.h"
"${CMAKE_CURRENT_LIST_DIR}/src/Visuals/HoloCoreGeometry.cpp"

    QML_FILES
        qml/Main.qml
)

target_link_libraries(NexusGui PRIVATE
    Qt6::Quick
    Qt6::Quick3D
)

set_target_properties(NexusGui PROPERTIES
    WIN32_EXECUTABLE TRUE
)
