cmake_minimum_required(VERSION 2.8.3)
project(bfx_cpp_api)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

#find_package(cryptopp)
find_package(CURL)

 

if(CURL_FOUND)
#include_directories(${CURL_INCLUDE_DIR})
#target_link_libraries(curltest ${CURL_LIBRARY})
message("${CURL_INCLUDE_DIR}", ${CURL_INCLUDE_DIR})
message("${CURL_LIBRARY}", ${CURL_LIBRARY})
else(CURL_FOUND)
message(FATAL_ERROR "curl not found!")
endif(CURL_FOUND)

 #include_directories(include)
 

# add_library(bfx_cpp_api  BitfinexAPI.cpp BitfinexAPI.hpp  withdraw.conf )

add_executable(bfx_cpp  example.cpp  BitfinexAPI.cpp BitfinexAPI.hpp  withdraw.conf)
target_link_libraries(bfx_cpp   libcryptopp.a  ${CURL_LIBRARY} )
