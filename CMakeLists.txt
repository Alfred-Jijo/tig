cmake_minimum_required(VERSION 3.13)
project(git-starter-cpp)
set(CMAKE_CXX_STANDARD 20) # Enable the C++20 standard

find_package(ZLIB REQUIRED) # Find the zlib package
find_package(OpenSSL REQUIRED) # Find the OpenSSL package
find_package(CURL REQUIRED) # Find the Curl package

# Add zlib_implement.cpp to the source files
set(SOURCE_FILES src/Server.cpp src/zlib_implement.cpp)

add_executable(server ${SOURCE_FILES})

if(ZLIB_FOUND)
    include_directories(${ZLIB_INCLUDE_DIRS}) # Include the zlib directories
    target_link_libraries(server ${ZLIB_LIBRARIES}) # Link the zlib libraries to your executable
endif()

if(OpenSSL_FOUND)
    include_directories(${OPENSSL_INCLUDE_DIR}) # Include the OpenSSL directories
    target_link_libraries(server ${OPENSSL_LIBRARIES}) # Link the OpenSSL libraries to your executable
endif()

if(CURL_FOUND)
    include_directories(${CURL_INCLUDE_DIRS}) # Include the Curl directories
    target_link_libraries(server ${CURL_LIBRARIES}) # Link the Curl libraries to your executable
endif()
