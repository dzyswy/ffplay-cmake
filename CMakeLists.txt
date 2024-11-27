cmake_minimum_required(VERSION 3.8)
project(ffplay-demo)



set(CMAKE_EXPORT_COMPILE_COMMANDS ON)


set(ENV{LD_LIBRARY_PATH} "/home/wy/src/ffmpeg/out/lib:$ENV{LD_LIBRARY_PATH}")
set(ENV{PKG_CONFIG_PATH} "/home/wy/src/ffmpeg/out/lib/pkgconfig:$ENV{PKG_CONFIG_PATH}")


# add_compile_options(-fpermissive)
# add_definitions(-D__STDC_CONSTANT_MACROS)

#find_package (glog REQUIRED)
#set(LIBS ${LIBS} glog::glog)

# 引入pkg-config模块
find_package(PkgConfig REQUIRED)

# 使用pkg-config查找FFmpeg库
pkg_check_modules(FFmpeg REQUIRED libavcodec libavformat libavutil libswscale libavdevice libavfilter libswresample libpostproc)
message(STATUS "find ffmpeg include: ${FFmpeg_INCLUDE_DIRS}")
message(STATUS "find ffmpeg lib: ${FFmpeg_LIBRARY_DIRS} ${FFmpeg_LIBRARIES}")


include_directories(${FFmpeg_INCLUDE_DIRS})

link_directories(${FFmpeg_LIBRARY_DIRS})

set(LIBS ${LIBS} ${FFmpeg_LIBRARIES})


find_package(SDL2 REQUIRED)
set(LIBS ${LIBS} SDL2::SDL2)
set(LIBS ${LIBS} m pthread)

include_directories(./)
include_directories(./src)
include_directories(/home/wy/src/ffmpeg/ffmpeg-6.0.1)



file(GLOB_RECURSE SOURCES "src/*.c")

# add_executable(ffmpeg ${SOURCES} ffmpeg.c)
# target_link_libraries (ffmpeg ${LIBS})

add_executable(ffplay ${SOURCES} ffplay.c)
target_link_libraries (ffplay ${LIBS})

add_executable(ffprobe ${SOURCES} ffprobe.c)
target_link_libraries (ffprobe ${LIBS})

 
 










