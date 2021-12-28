cmake_minimum_required(VERSION 3.2)

project(helloworld)

set(PROJECT_VERSION_MAJOR 0)
set(PROJECT_VERSION_MINOR 0)

add_executable(helloworld_cli main.cxx)

set_target_properties(helloworld_cli PROPERTIES
	CXX_STANDARD 14
	CXX_STANDARD_REQUIRED ON)
target_compile_definitions(helloworld_cli PRIVATE BUILD_VERSION=$ENV{BUILD_VERSION})

target_compile_options(helloworld_cli PRIVATE
	-Wall -Wextra -pedantic -Werror)

install(TARGETS helloworld_cli RUNTIME DESTINATION bin)

set(CPACK_GENERATOR DEB)
set(CPACK_PACKAGE_VERSION_MAJOR "${PROJECT_VERSION_MAJOR}")
set(CPACK_PACKAGE_VERSION_MINOR "${PROJECT_VERSION_MINOR}")
set(CPACK_PACKAGE_VERSION_PATCH $ENV{BUILD_VERSION})
set(CPACK_PACKAGE_CONTACT hit@me.com)
include(CPack)
