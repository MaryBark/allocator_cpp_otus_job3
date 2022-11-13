cmake_minimum_required(VERSION 3.2)

project(allocator1 VERSION 0.0.${PATCH_VERSION})

#if($ENV{TRAVIS_BUILD_NUMBER})
#    project(allocator1 VERSION 0.0.$ENV{TRAVIS_BUILD_NUMBER})
#else()
#    project(allocator1 VERSION 0.0.1)
#endif()

configure_file(version.h.in version.h)

add_executable(allocator1 main.cpp alloc.cpp alloc.h linked_list.h)

set_target_properties(allocator1 PROPERTIES
        CXX_STANDARD 14
        CXX_STANDARD_REQUIRED ON
        COMPILE_OPTIONS "-Wpedantic;-Wall;-Wextra"
        )

install(TARGETS allocator1 RUNTIME DESTINATION bin)

set(CPACK_GENERATOR DEB)

set(CPACK_PACKAGE_VERSION_MAJOR "${PROJECT_VERSION_MAJOR}")
set(CPACK_PACKAGE_VERSION_MINOR "${PROJECT_VERSION_MINOR}")
set(CPACK_PACKAGE_VERSION_PATCH "${PROJECT_VERSION_PATCH}")

# не знаю, на фига это надо, но в первой лекции было
set(CPACK_PACKAGE_CONTACT Alttaira@yandex.ru)

# тесты не буду делать(((
include(CPack)
