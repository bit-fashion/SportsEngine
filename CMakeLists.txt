#/ -------------------------------------------------------------------------------- \#
#|                                                                                  |#
#|    Copyright (C) 2023 bit-fashion                                                |#
#|                                                                                  |#
#|    This program is free software: you can redistribute it and/or modify          |#
#|    it under the terms of the GNU General Public License as published by          |#
#|    the Free Software Foundation, either version 3 of the License, or             |#
#|    (at your option) any later version.                                           |#
#|                                                                                  |#
#|    This program is distributed in the hope that it will be useful,               |#
#|    but WITHOUT ANY WARRANTY; without even the implied warranty of                |#
#|    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the                 |#
#|    GNU General Public License for more details.                                  |#
#|                                                                                  |#
#|    You should have received a copy of the GNU General Public License             |#
#|    along with this program.  If not, see <https://www.gnu.org/licenses/>.        |#
#|                                                                                  |#
#|    This program comes with ABSOLUTELY NO WARRANTY; for details type `show w'.    |#
#|    This is free software, and you are welcome to redistribute it                 |#
#|    under certain conditions; type `show c' for details.                          |#
#|                                                                                  |#
#\ -------------------------------------------------------------------------------- /#

# //////////////////////////////////////////////////////////////////////////////////////
# ///
# /// File:           CMakeLists.txt
# /// Create Time:    2023/12/27 16:47
# /// Author:         bit-fashion
# /// EMail:          bit-fashion@hotmail.com
# ///
# //////////////////////////////////////////////////////////////////////////////////////
CMAKE_MINIMUM_REQUIRED(VERSION 3.26)
PROJECT(SportsEngine)

SET(CMAKE_CXX_STANDARD 23)

FIND_PACKAGE(Vulkan REQUIRED)
IF(Vulkan_FOUND)
    MESSAGE(STATUS "Vulkan include dir: ${Vulkan_INCLUDE_DIR}")
    MESSAGE(STATUS "Vulkan library path: ${Vulkan_LIBRARY}")
ENDIF()

INCLUDE_DIRECTORIES(SYSTEM
  ${PROJECT_SOURCE_DIR}/Source/Include
  ${PROJECT_SOURCE_DIR}/Source/ThirdParty/GLFW/include
)

LINK_DIRECTORIES(${PROJECT_NAME}
  ${PROJECT_SOURCE_DIR}/Source/ThirdParty/GLFW/lib-mingw-w64
)

ADD_EXECUTABLE(${PROJECT_NAME}
  ${PROJECT_SOURCE_DIR}/Source/Runtime/main.cpp
  ${PROJECT_SOURCE_DIR}/Source/Runtime/Window/Window.cpp
)

TARGET_LINK_LIBRARIES(${PROJECT_NAME}
  glfw3
  ${Vulkan_LIBRARY}
)