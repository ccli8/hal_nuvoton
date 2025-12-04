# SPDX-License-Identifier: Apache-2.0
#
# Copyright (c) 2025 Nuvoton Technology Corporation.

if(CONFIG_HAS_NUMAKER_STDDRIVER)
    # Add all StdDriver "*.c" files recursively
    FILE(GLOB_RECURSE stddriver_sources
        RELATIVE ${CMAKE_CURRENT_SOURCE_DIR}
        "${CMAKE_CURRENT_SOURCE_DIR}/*.c"
    )

    # Exclude unsupported files
    list(REMOVE_ITEM stddriver_sources
        src/i3c.c
        src/retarget.c
    )

    zephyr_library_sources(${stddriver_sources})
    return()
endif()

zephyr_library_sources(src/clk.c)
zephyr_library_sources_ifdef(CONFIG_HAS_NUMAKER_HAL src/sys.c)
zephyr_library_sources_ifdef(CONFIG_HAS_NUMAKER_FMC src/fmc.c)
zephyr_library_sources_ifdef(CONFIG_HAS_NUMAKER_GPIO src/gpio.c)
zephyr_library_sources_ifdef(CONFIG_HAS_NUMAKER_UART src/uart.c)
zephyr_library_sources_ifdef(CONFIG_HAS_NUMAKER_I2C src/i2c.c)
zephyr_library_sources_ifdef(CONFIG_HAS_NUMAKER_SPI src/spi.c)
zephyr_library_sources_ifdef(CONFIG_HAS_NUMAKER_SPI src/qspi.c)
zephyr_library_sources_ifdef(CONFIG_HAS_NUMAKER_PWM src/epwm.c)
zephyr_library_sources_ifdef(CONFIG_HAS_NUMAKER_USBD src/hsusbd.c)
zephyr_library_sources_ifdef(CONFIG_HAS_NUMAKER_CANFD src/canfd.c)
zephyr_library_sources_ifdef(CONFIG_HAS_NUMAKER_ADC src/eadc.c)
zephyr_library_sources_ifdef(CONFIG_HAS_NUMAKER_RTC src/rtc.c)
zephyr_library_sources_ifdef(CONFIG_HAS_NUMAKER_TMR src/timer.c)
