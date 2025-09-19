cmake_minimum_required(VERSION 3.15)
project(Lab3)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(PkgConfig REQUIRED)
pkg_check_modules(SDL2 REQUIRED sdl2)
pkg_check_modules(SDL2_TTF REQUIRED SDL2_ttf)

add_executable(app 
    main.cpp
    Dialog.cpp
    Menu.cpp
    MenuItem.cpp
    MenuSystem.cpp
    ResourceLoader.cpp
)

target_include_directories(app PRIVATE ${SDL2_INCLUDE_DIRS} ${SDL2_TTF_INCLUDE_DIRS})
target_link_libraries(app PRIVATE ${SDL2_LIBRARIES} ${SDL2_TTF_LIBRARIES})
target_compile_options(app PRIVATE ${SDL2_CFLAGS_OTHER} ${SDL2_TTF_CFLAGS_OTHER})

# Для Windows добавим необходимые библиотеки
if(WIN32)
    target_link_libraries(app PRIVATE mingw32)
endif()

set(SOURCES
    main.cpp
    Dialog.cpp
    Menu.cpp
    MenuItem.cpp
    MenuSystem.cpp
    ResourceLoader.cpp
    Dialog.h
    Menu.h
    MenuItem.h
    MenuSystem.h
    ResourceLoader.h
)

source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${SOURCES})