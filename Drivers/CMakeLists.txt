INCLUDE(CMakeForceCompiler)

# CROSS COMPILER SETTING
SET(CMAKE_SYSTEM_NAME Generic)
CMAKE_MINIMUM_REQUIRED (VERSION 2.6)

include_directories(BSP/STM32F4xx_Nucleo_144)
include_directories(CMSIS/Include)
include_directories(CMSIS/Device/ST/STM32F4xx/Include)
include_directories(STM32F4xx_HAL_Driver/Inc)
include_directories(STM32F4xx_HAL_Driver/Inc/Legacy)


set (HAL_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/STM32F4xx_HAL_Driver/Src)
set (BSP_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/BSP/STM32F4xx_Nucleo_144)

if (CMAKE_C_COMPILER_ID STREQUAL "GNU")
    set(BOARD_SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/CMSIS/Device/ST/STM32F4xx/Source/Templates/gcc/startup_stm32f429xx.s)
elseif (CMAKE_C_COMPILER_ID STREQUAL "ARMCC")
    list(APPEND Additional_SRC ${PORTING_SOURCE_DIR}/startup_stm32f429xx.s )
    set (Additional_SRC ${Additional_SRC} PARENT_SCOPE)
endif()


file(GLOB DRIVERS_SRCS  
	${CMAKE_CURRENT_SOURCE_DIR}/system_stm32f4xx.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_eth.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_rng.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_rtc.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_rtc_ex.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_tim.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_tim_ex.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_rcc.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_rcc_ex.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_flash.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_flash_ex.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_flash_ramfunc.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_gpio.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_dma.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_dma_ex.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_pwr.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_pwr_ex.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_cortex.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_exti.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_ltdc.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_i2c.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_sdram.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_spi.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_uart.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_i2c_ex.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_dma2d.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_sai.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_sai_ex.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal_hcd.c
	${HAL_SOURCE_DIR}/stm32f4xx_hal.c
	${HAL_SOURCE_DIR}/stm32f4xx_ll_fmc.c
	${HAL_SOURCE_DIR}/stm32f4xx_ll_usb.c
	${HAL_SOURCE_DIR}/stm32f4xx_ll_sdmmc.c
	${BSP_SOURCE_DIR}/*.c
)

list(APPEND DRIVERS_SRCS ${BOARD_SOURCES})


add_library(board STATIC ${DRIVERS_SRCS})

