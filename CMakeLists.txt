# TouchPass Fingerprint Driver (adapted from razilyis/zmk-module-Fingerprint)

if(CONFIG_ZMK_TOUCHPASS)
    zephyr_library()
    zephyr_library_sources(
        src/touchpass/fingerprint_driver.c
        src/touchpass/behavior_touchpass.c
    )
    zephyr_library_sources_ifdef(CONFIG_NVS src/touchpass/storage.c)
    zephyr_library_sources_ifdef(CONFIG_ZMK_TOUCHPASS_SERIAL_RPC src/touchpass/serial_rpc.c)

    zephyr_include_directories(include)
    zephyr_include_directories(${APPLICATION_SOURCE_DIR}/include)

    zephyr_library_link_libraries(zephyr_interface)
endif()
