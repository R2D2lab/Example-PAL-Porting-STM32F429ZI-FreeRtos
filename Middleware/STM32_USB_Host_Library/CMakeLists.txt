INCLUDE(CMakeForceCompiler)

# CROSS COMPILER SETTING
SET(CMAKE_SYSTEM_NAME Generic)
CMAKE_MINIMUM_REQUIRED (VERSION 2.6)


include_directories(Core/Inc)
include_directories(Class/MSC/Inc)
include_directories(Class/CDC/Inc)
include_directories(Class/HID/Inc)
include_directories(Class/MTP/Inc)
##include_directories(../../PORTING)

set (USBH_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/)

set(USBH_SRCS 
${USBH_SOURCE_DIR}/Core/Src/usbh_core.c
${USBH_SOURCE_DIR}/Core/Src/usbh_ctlreq.c
${USBH_SOURCE_DIR}/Core/Src/usbh_ioreq.c
${USBH_SOURCE_DIR}/Core/Src/usbh_pipes.c
${USBH_SOURCE_DIR}/Class/MSC/Src/usbh_msc.c
${USBH_SOURCE_DIR}/Class/MSC/Src/usbh_msc_bot.c
${USBH_SOURCE_DIR}/Class/MSC/Src/usbh_msc_scsi.c
)


add_library(usbhost STATIC ${USBH_SRCS})

