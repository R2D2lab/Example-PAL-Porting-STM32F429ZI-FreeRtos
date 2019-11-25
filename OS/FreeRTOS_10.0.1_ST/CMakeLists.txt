# CROSS COMPILER SETTINGS
cmake_minimum_required (VERSION 2.8)
SET(CMAKE_SYSTEM_NAME Generic)


include_directories(Source/include)
include_directories(Source/CMSIS_RTOS)
include_directories(../../Drivers/PORTING)

SET(RTOS_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/Source)

SET(FreeRTOS_SRCS
        ${RTOS_SOURCE_DIR}/event_groups.c
        ${RTOS_SOURCE_DIR}/croutine.c
        ${RTOS_SOURCE_DIR}/list.c
        ${RTOS_SOURCE_DIR}/queue.c
        ${RTOS_SOURCE_DIR}/tasks.c
        ${RTOS_SOURCE_DIR}/timers.c
        ${RTOS_SOURCE_DIR}/stream_buffer.c
        ${RTOS_SOURCE_DIR}/CMSIS_RTOS/cmsis_os.c
        ${RTOS_SOURCE_DIR}/portable/MemMang/heap_3.c
)

if (CMAKE_C_COMPILER_ID STREQUAL "GNU")
    SET(PORT_DIR ${CMAKE_CURRENT_LIST_DIR}/Source/portable/GCC)
elseif (CMAKE_C_COMPILER_ID STREQUAL "ARMCC")
    SET(PORT_DIR ${CMAKE_CURRENT_LIST_DIR}/Source/portable/RVDS)
endif()

if(CPU STREQUAL "ARM Cortex-M0")
    list(APPEND FreeRTOS_SRCS ${PORT_DIR}/ARM_CM0/port.c)
elseif(CPU STREQUAL "ARM Cortex-M0plus")
    list(APPEND FreeRTOS_SRCS ${PORT_DIR}/ARM_CM0/port.c)
elseif(CPU STREQUAL "ARM Cortex-M3")
    list(APPEND FreeRTOS_SRCS ${PORT_DIR}/ARM_CM3/port.c)
elseif(CPU STREQUAL "cortex-m4")
    list(APPEND FreeRTOS_SRCS ${PORT_DIR}/ARM_CM4F/port.c)
elseif(CPU STREQUAL "ARM Cortex-M7")
    list(APPEND FreeRTOS_SRCS ${PORT_DIR}/ARM_CM7/r0p1/port.c)
else()
    message(FATAL_ERROR "CPU not supported.")
endif()

add_library(FreeRTOS STATIC ${FreeRTOS_SRCS})
