cmake_minimum_required(VERSION 3.20.0)
cmake_policy(SET CMP0114 NEW)

project(gfx-sandbox)
if(PROJECT_IS_TOP_LEVEL)
  # Output to /bin
  string(TOUPPER ${CMAKE_BUILD_TYPE} CONFIG_NAME)
  set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_${CONFIG_NAME} ${CMAKE_BINARY_DIR}/bin)
  message(STATUS "CMAKE_RUNTIME_OUTPUT_DIRECTORY_${CONFIG_NAME}=${CMAKE_RUNTIME_OUTPUT_DIRECTORY_${CONFIG_NAME}}")

  set(SHARDS_ROOT ../shards CACHE FILEPATH "Path to shards project root")
  include(${SHARDS_ROOT}/cmake/Root.cmake)
endif()

add_executable(gfx-sandbox sandbox.cpp)
target_link_libraries(gfx-sandbox gfx gfx-texture-file gfx-gltf)
