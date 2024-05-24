cmake_minimum_required(VERSION 3.24)


option(CMAKE_COMPILE_WARNING_AS_ERROR "Enable warnings-as-error" ON)
option(HALST_INCLUDE_DEFAULT_INIT "Include default initialization code; turn off when providing custom initialization" ON)
option(HALST_BUILD_EXAMPLES "Enable build of the examples" ON)
option(HALST_BUILD_EXAMPLES_FREERTOS "Enable build of the FreeRTOS example" OFF)
set(HALST_XML_GPIO "" CACHE STRING "XML GPIO table")
set(HALST_XML_STM32 "" CACHE STRING "XML STM32 table")

include(FetchContent)

FetchContent_Declare(
    emil
    GIT_REPOSITORY https://github.com/philips-software/embeddedinfralib.git
    GIT_TAG        main
)

FetchContent_Declare(
    halst
    GIT_REPOSITORY https://github.com/philips-software/amp-hal-st.git
    GIT_TAG        main
)

FetchContent_MakeAvailable(emil halst)

project(myproject LANGUAGES C CXX ASM VERSION 3.0.0) # x-release-please-version

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED On)

set_directory_properties(PROPERTY USE_FOLDERS ON)

add_subdirectory(src)

include(CPack)
