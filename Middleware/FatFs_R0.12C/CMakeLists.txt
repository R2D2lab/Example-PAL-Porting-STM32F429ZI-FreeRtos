INCLUDE(CMakeForceCompiler)

# CROSS COMPILER SETTING
SET(CMAKE_SYSTEM_NAME Generic)
CMAKE_MINIMUM_REQUIRED (VERSION 2.6)


include_directories(src/option)
include_directories(src)
##include_directories(../../PORTING)

set (FATFS_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/src)

set(FATFS_SRCS 
${FATFS_SOURCE_DIR}/diskio.c
${FATFS_SOURCE_DIR}/ff.c
${FATFS_SOURCE_DIR}/ff_gen_drv.c
${FATFS_SOURCE_DIR}/option/syscall.c
)


add_library(fatfs STATIC ${FATFS_SRCS})

