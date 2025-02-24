cmake_minimum_required(VERSION 3.20)
project(cpp_sdl2)
set(CMAKE_CXX_STANDARD 11)

# 查找SDL2库
find_package(SDL2 REQUIRED)
find_package(SDL2_image REQUIRED)
find_package(SDL2_ttf REQUIRED)
find_package(SDL2_mixer REQUIRED)
find_package(lua REQUIRED)
# find_package(bz2 REQUIRED)
find_package(fontconfig REQUIRED)
# find_package(smpeg2 REQUIRED)
# find_package(libjpeg REQUIRED)
# find_package(libogg REQUIRED)
# find_package(libvorbis_dev REQUIRED)
# 添加SDL头文件搜索路径
include_directories(${SDL2_INCLUDE_DIRS})
include_directories(${SDL2_IMAGE_INCLUDE_DIRS})
include_directories(${SDL2_MIXER_INCLUDE_DIRS})
include_directories(${LUA_INCLUDE_DIRS})
include_directories(${BZ2_IMAGE_INCLUDE_DIRS})
include_directories(${FONTCONFIG_IMAGE_INCLUDE_DIRS})
include_directories(${SMPEG2_IMAGE_INCLUDE_DIRS})
include_directories(${LIBJPEG_IMAGE_INCLUDE_DIRS})
include_directories(${LIBOGG_IMAGE_INCLUDE_DIRS})
include_directories(${LIBVORBIS_DEV_IMAGE_INCLUDE_DIRS})

include_directories(${SDL2_TTF_INCLUDE_DIRS} ./builtin_dll ./simd)

# 查找TextureHandle目录下的所有cpp文件
file(GLOB_RECURSE ASTCPP ./*.cpp)
file(GLOB_RECURSE built ./builtin_dll/*.cpp)
file(GLOB_RECURSE smid ./smid/*.cpp)

# 增加SDL链接库目录
link_libraries(${SDL2_LIBRARIES})
link_libraries(SDL2_image::SDL2_image)
link_libraries(SDL2_ttf::SDL2_ttf)
link_libraries(SDL2_ttf::SDL2_ttf SDL2_mixer::SDL2_mixer)
# 添加可执行文件
add_executable(cpp_sdl2 ${ASTCPP} ${build} ${smid})