cmake_minimum_required(VERSION 3.10.2)

add_library(
        native-lib


        SHARED


        native-lib.cpp)


find_library(
        log-lib


        log)


include_directories(include)

set(libs ${CMAKE_SOURCE_DIR}/libs/${ANDROID_ABI})
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -L${libs}")

target_link_libraries(
        native-lib

        avfilter avformat avcodec avutil swresample swscale


        ${log-lib})