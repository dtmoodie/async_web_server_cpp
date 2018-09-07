cmake_minimum_required(VERSION 2.8.3)
project(async_web_server_cpp)

## System dependencies are found with CMake's conventions
find_package(Boost REQUIRED COMPONENTS thread system regex filesystem)
find_package(OpenSSL)

###########
## Build ##
###########

## Specify additional locations of header files
include_directories(
  include
  ${Boost_INCLUDE_DIRS}
  ${OPENSSL_INCLUDE_DIRS}
)

add_library(${PROJECT_NAME} src/http_server.cpp
  src/http_connection.cpp src/http_request_parser.cpp
  src/http_reply.cpp src/http_request_handler.cpp
  src/websocket_connection.cpp src/websocket_request_handler.cpp
  src/websocket_message.cpp src/http_request.cpp)

target_link_libraries(${PROJECT_NAME}
  ${OPENSSL_LIBRARIES}
  ${Boost_LIBRARIES}
)

