add_executable(myprogram Main.cpp)

target_link_libraries(myprogram PUBLIC
    infra.event
    hal_st.stm32fxxx
)

emil_build_for(myprogram
    TARGET_MCU stm32f429
    TARGET_MCU stm32f746
    TARGET_MCU stm32f767
    PREREQUISITE_BOOL HALST_BUILD_EXAMPLES
)

target_compile_definitions(myprogram PUBLIC
    NUCLEO=Nucleo144Ui
)


halst_target_default_linker_scripts(myprogram)
halst_target_default_init(myprogram)

emil_generate_artifacts(TARGET myprogram LST MAP BIN HEX)