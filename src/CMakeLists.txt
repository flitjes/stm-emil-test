#add_executable(src.blink_144 Main.cpp)
#emil_build_for(src.blink_144
#    TARGET_MCU stm32f429
#    TARGET_MCU stm32f746
#    TARGET_MCU stm32f767
#    PREREQUISITE_BOOL HALST_BUILD_EXAMPLES
#)

#target_compile_definitions(src.blink_144 PUBLIC
#    NUCLEO=Nucleo144Ui
#)

#target_link_libraries(src.blink_144 PRIVATE
#    services.util
#    hal_st.instantiations
#)

#halst_target_default_linker_scripts(src.blink_144)
#halst_target_default_init(src.blink_144)

#emil_generate_artifacts(TARGET src.blink_144 LST MAP BIN HEX)

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