add_executable(myprogram Main.cpp)
emil_build_for(myprogram TARGET_MCU_VENDOR st PREREQUISITE_BOOL HALST_BUILD_EXAMPLES)

target_compile_definitions(myprogram PUBLIC
    NUCLEO=Nucleo64Ui
)

target_link_libraries(myprogram PRIVATE
    services.util
    hal_st.instantiations
)

halst_target_default_linker_scripts(myprogram)
halst_target_default_init(myprogram)

emil_generate_artifacts(TARGET myprogram LST MAP BIN HEX)