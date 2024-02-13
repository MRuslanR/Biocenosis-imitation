cmake_minimum_required(VERSION 3.14)
project(Biocenosis_imitation)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
set(SOURCE_FILES main.cpp)
add_executable(Biocenosis_imitation ${SOURCE_FILES})

if(WIN32)
    set(SFML_ROOT "C:\\SFML-2.6.1")
    set(SFML_STATIC_LIBRARIES TRUE)
else()
    include_directories(/usr/local/include)
endif()

# Поиск компонентов библиотеки
find_package(SFML 2.6.1 COMPONENTS graphics window system REQUIRED)

if(SFML_FOUND)
    # Добавление headers
    target_include_directories(Biocenosis_imitation PRIVATE ${SFML_INCLUDE_DIR})
    # Линковка библиотек
    target_link_libraries(Biocenosis_imitation PRIVATE m sfml-graphics sfml-window sfml-system)
endif()
