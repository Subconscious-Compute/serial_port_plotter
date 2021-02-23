cmake_minimum_required(VERSION 3.12)

project(serial_port_plotter VERSION 1.3.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_INCLUDE_CURRENT_DIR ON)

find_package(Qt5 COMPONENTS Widgets SerialPort PrintSupport REQUIRED)

add_executable(serial_port_plotter
    main.cpp
    qcustomplot/qcustomplot.cpp
    mainwindow.cpp
    helpwindow.cpp
    res/serial_port_plotter.rc
    # make sure that you have updated the git submodules 
    res/qdark_stylesheet/qdarkstyle/style.qrc
    res/serial_port_plotter.qrc
)

target_include_directories(serial_port_plotter PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})

target_link_libraries(serial_port_plotter Qt5::Widgets Qt5::SerialPort
    Qt5::PrintSupport)

# install
install(TARGETS serial_port_plotter DESTINATION bin)
