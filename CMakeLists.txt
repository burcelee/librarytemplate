cmake_minimum_required(VERSION 3.26.0)

project (librarytemplate)

file(GLOB_RECURSE librarytemplate_headers ${CMAKE_CURRENT_SOURCE_DIR}/include/*.h)
file(GLOB_RECURSE librarytemplate_sources ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp)

source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${librarytemplate_headers})
source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${librarytemplate_sources})

add_library (librarytemplate STATIC  ${librarytemplate_sources} ${librarytemplate_headers})
target_include_directories(librarytemplate PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)
target_compile_features(librarytemplate PUBLIC cxx_std_17)

if(MSVC)
  add_compile_options(/W4 /WX)
else()
  add_compile_options(-Wall -Wextra -Wpedantic -Werror)
endif()