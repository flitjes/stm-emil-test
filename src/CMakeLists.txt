add_executable(src.blink_144 Main.cpp)
emil_build_for(src.blink_144
    TARGET_MCU stm32f429
    TARGET_MCU stm32f746
    TARGET_MCU stm32f767
    PREREQUISITE_BOOL HALST_BUILD_EXAMPLES
)

target_compile_definitions(src.blink_144 PUBLIC
    NUCLEO=Nucleo144Ui
)

target_link_libraries(src.blink_144 PRIVATE
    services.util
    hal_st.instantiations
)

halst_target_default_linker_scripts(src.blink_144)
halst_target_default_init(src.blink_144)

emil_generate_artifacts(TARGET src.blink_144 LST MAP BIN HEX)

######################################################################

add_executable(src.blink_64 Main.cpp)
emil_build_for(src.blink_64
    TARGET_MCU stm32g431
    TARGET_MCU stm32g474
    TARGET_MCU stm32wb55
    PREREQUISITE_BOOL HALST_BUILD_EXAMPLES
)

target_compile_definitions(src.blink_64 PUBLIC
    $<$<NOT:$<STREQUAL:${TARGET_MCU},stm32wb55>>:NUCLEO=Nucleo64Ui>
    $<$<STREQUAL:${TARGET_MCU},stm32wb55>:NUCLEO=Nucleo64WBUi>
)

target_link_libraries(src.blink_64 PRIVATE
    services.util
    hal_st.instantiations
)

halst_target_default_linker_scripts(src.blink_64)
halst_target_default_init(src.blink_64)

emil_generate_artifacts(TARGET src.blink_64 LST MAP BIN HEX)