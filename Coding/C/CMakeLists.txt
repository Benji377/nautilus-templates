# =============================================================================
# Initialization
# =============================================================================

cmake_minimum_required(VERSION 2.9)
project(main C)

# =============================================================================
# Project dependencies
# =============================================================================

# -----------------------------------------------------------------------------
# OpenGL
# -----------------------------------------------------------------------------
#set(OpenGL_GL_PREFERENCE LEGACY)
#find_package(OpenGL REQUIRED)
#find_package(GLUT REQUIRED)
#include_directories(${OPENGL_INCLUDE_DIRS} ${GLUT_INCLUDE_DIR})

# =============================================================================
# Build process
# =============================================================================

# -----------------------------------------------------------------------------
# Source files
# -----------------------------------------------------------------------------

# Set compiler parameters
set(CMAKE_C_STANDARD 90)
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -s -Wall -Wextra -Wpedantic")

# Sources
file(GLOB SRC_FILES *.c *.h)

# Compile the main executable
add_executable(${CMAKE_PROJECT_NAME} ${SRC_FILES})
#target_link_libraries(${CMAKE_PROJECT_NAME} SOIL ${OPENGL_LIBRARIES} ${GLUT_LIBRARY} SDL2main SDL2 SDL2_mixer m)

# =============================================================================
# Install process
# =============================================================================

# Define the files location during install process
install(TARGETS ${CMAKE_PROJECT_NAME} DESTINATION "bin")

# =============================================================================
# Custom targets
# =============================================================================

# Define the 'run' target
add_custom_target(run
    COMMAND ${CMAKE_PROJECT_NAME}
    DEPENDS ${CMAKE_PROJECT_NAME}
    WORKING_DIRECTORY ${CMAKE_PROJECT_DIR}
)