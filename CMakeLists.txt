cmake_minimum_required(VERSION 3.31)
project(test_log)

set(CMAKE_CXX_STANDARD 20)

# Using FetchContent (download automatically) the custom_spdlog library
 include(FetchContent)
 FetchContent_Declare(
     custom_spdlog
     GIT_REPOSITORY https://github.com/raymondtruongdev/custom_spdlog.git
     GIT_TAG master  # or specific version tag
 )
 FetchContent_MakeAvailable(custom_spdlog)
 
 # Show message inform PULL 'custom_spdlog' from Github  if it DOSE NOT exist in source directory
 FetchContent_GetProperties(custom_spdlog)
 if( NOT EXISTS "${custom_spdlog_SOURCE_DIR}")
     message(STATUS "🔄 Pull 'custom_spdlog' library from https://github.com/raymondtruongdev/custom_spdlog.git")
 endif()

# Create the executable first
add_executable(test_log main.cpp)

# Then link with custom_spdlog
target_link_libraries(test_log PRIVATE custom_spdlog::custom_spdlog)


