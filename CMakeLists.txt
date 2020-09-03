cmake_minimum_required(VERSION 2.8.11)

project(QtVtkViewer)

set(CMAKE_CONFIGURATION_TYPES "Debug;Release")
set(CMAKE_INCLUDE_CURRENT_DIR ON)

# List source files & resources
file (GLOB Sources *.cpp)
file (GLOB_RECURSE Headers *.h)
file (GLOB_RECURSE Resources *.qrc)
file (GLOB_RECURSE UIs *.ui)

# Find package Qt
find_package(Qt5Core REQUIRED)
find_package(Qt5Gui REQUIRED)
find_package(Qt5Widgets REQUIRED)
find_package(Qt5OpenGL REQUIRED)

# Use Qt
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)

# Find package VTK
find_package(VTK REQUIRED)

# Use VTK
#include(${VTK_USE_FILE})
include_directories(${VTK_INCLUDE_DIRS})

# Build executable
add_executable(QtVtkViewer WIN32 ${Sources} ${Headers} ${Resources} ${UIs})

# Link libraries
target_link_libraries(QtVtkViewer Qt5::Widgets Qt5::OpenGL ${VTK_LIBRARIES})
