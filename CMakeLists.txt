cmake_minimum_required(VERSION 3.21)

project(MyProject VERSION 1.0.0)

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


set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED On)

set_directory_properties(PROPERTY USE_FOLDERS ON)

add_subdirectory(src)

#emil_clangformat_directories(stm32-devcontainer-template DIRECTORIES ./src)
emil_folderize_all_targets()


