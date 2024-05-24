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

add_executable(hal_st.myprogram Main.cpp)

emil_build_for(hal_st.myprogram
    TARGET_MCU stm32f429
    TARGET_MCU stm32f746
    TARGET_MCU stm32f767
    PREREQUISITE_BOOL HALST_BUILD_EXAMPLES
)

target_link_libraries(hal_st.myprogram PRIVATE
    infra.event
    hal_st.stm32fxxx
)

target_compile_definitions(hal_st.myprogram PUBLIC
    NUCLEO=Nucleo144Ui
)

halst_target_default_linker_scripts(hal_st.myprogram)
halst_target_default_init(hal_st.myprogram)

emil_generate_artifacts(TARGET hal_st.myprogram LST MAP BIN HEX)