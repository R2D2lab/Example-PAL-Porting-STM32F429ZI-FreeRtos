INCLUDE(CMakeForceCompiler)

# CROSS COMPILER SETTING
SET(CMAKE_SYSTEM_NAME Generic)
CMAKE_MINIMUM_REQUIRED (VERSION 2.6)

#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../Drivers/STM32F4xx_Nucleo_144)
#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../Drivers/CMSIS/Include)
#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../Drivers/CMSIS/Device/ST/STM32F4xx/Include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../Drivers/STM32F4xx_HAL_Driver/Inc)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../Drivers/STM32F4xx_HAL_Driver/Inc/Legacy)


set (PORTING_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR})


set(DRIVERS_SRCS 
	${PORTING_SOURCE_DIR}/stm32f4xx_hal_msp.c
	${PORTING_SOURCE_DIR}/stm32f4xx_hal_timebase_tim.c
	${PORTING_SOURCE_DIR}/stm32f4xx_it.c	
	${PORTING_SOURCE_DIR}/usbh_conf.c
	${PORTING_SOURCE_DIR}/usbh_diskio_dma.c
)


add_library(f429port STATIC ${DRIVERS_SRCS})
get_property(f429_location TARGET f429port PROPERTY LOCATION)
target_link_libraries(f429port -Wl,--whole-archive ${f429_location} -Wl,--no-whole-archive board)
target_link_libraries(f429port board)
