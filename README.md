# Example-PAL-Porting-STM32F429ZI-FreeRtos

0. Switch to this README PATH.

1, Copy from SDK: STM32Cube_FW_F4_V1.24.0\Drivers\* contents to .\Drivers folder. 

2, Copy from SDK: STM32Cube_FW_F4_V1.24.0\Middlewares\Third_Party\FreeRTOS\* contents to .\OS\FreeRTOS_10.0.1_ST folder.

3, Copy from SDK: 
STM32Cube_FW_F4_V1.24.0\Middlewares\Third_Party\FatFs\* contents to .\Middleware\FatFs_R0.12C folder.

4, Copy from SDK:
STM32Cube_FW_F4_V1.24.0\Middlewares\Third_Party\LwIP\* contents to .\Middleware\LwIP_2.0.3 folder.

5, Copy from SDK: 
STM32Cube_FW_F4_V1.24.0\Middlewares\ST\STM32_USB_Host_Library\* contents to .\Middleware\STM32_USB_Host_Library folder.

6, Final Folder Tree:

.
├── Drivers
│   ├── BSP
│   │   ├── Adafruit_Shield
│   │   ├── Components
│   │   ├── STM32412G-Discovery
│   │   ├── STM32446E_EVAL
│   │   ├── STM32469I-Discovery
│   │   ├── STM32469I_EVAL
│   │   ├── STM324x9I_EVAL
│   │   ├── STM324xG_EVAL
│   │   ├── STM32F401-Discovery
│   │   ├── STM32F411E-Discovery
│   │   ├── STM32F413H-Discovery
│   │   ├── STM32F429I-Discovery
│   │   ├── STM32F4-Discovery
│   │   ├── STM32F4xx-Nucleo
│   │   └── STM32F4xx_Nucleo_144
│   ├── CMakeLists.txt
│   ├── CMSIS
│   │   ├── ARM.CMSIS.pdsc
│   │   ├── Core
│   │   ├── Core_A
│   │   ├── Device
│   │   ├── docs
│   │   ├── DSP
│   │   ├── Include
│   │   ├── Lib
│   │   ├── LICENSE.txt
│   │   ├── NN
│   │   ├── README.md
│   │   ├── RTOS
│   │   └── RTOS2
│   ├── STM32F4xx_HAL_Driver
│   │   ├── Inc
│   │   ├── Release_Notes.html
│   │   ├── Src
│   │   ├── STM32F410Rx_User_Manual.chm
│   │   ├── STM32F411xE_User_Manual.chm
│   │   ├── STM32F412Zx_User_Manual.chm
│   │   ├── STM32F417xx_User_Manual.chm
│   │   ├── STM32F423xx_User_Manual.chm
│   │   ├── STM32F439xx_User_Manual.chm
│   │   ├── STM32F446xx_User_Manual.chm
│   │   └── STM32F479xx_User_Manual.chm
│   └── system_stm32f4xx.c
├── Middleware
│   ├── FatFs_R0.12C
│   │   ├── CMakeLists.txt
│   │   ├── doc
│   │   └── src
│   ├── LwIP_2.0.3
│   │   ├── CHANGELOG
│   │   ├── CMakeLists.txt
│   │   ├── COPYING
│   │   ├── doc
│   │   ├── FILES
│   │   ├── port
│   │   ├── README
│   │   ├── src
│   │   ├── st_readme.txt
│   │   ├── system
│   │   ├── test
│   │   └── UPGRADING
│   └── STM32_USB_Host_Library
│       ├── Class
│       ├── CMakeLists.txt
│       ├── Core
│       └── Release_Notes.html
├── OS
│   └── FreeRTOS_10.0.1_ST
│       ├── CMakeLists.txt
│       ├── License
│       ├── links_to_doc_pages_for_the_demo_projects.url
│       ├── readme.txt
│       └── Source
├── PORTING
│   ├── CMakeLists.txt
│   ├── ffconf.h
│   ├── FreeRTOSConfig.h
│   ├── porting.h
│   ├── stm32f4xx_hal_conf.h
│   ├── stm32f4xx_hal_msp.c
│   ├── stm32f4xx_hal_timebase_tim.c
│   ├── stm32f4xx_it.c
│   ├── stm32f4xx_it.h
│   ├── TOOLCHAIN_ARM_STD
│   │   ├── startup_stm32f429xx.S
│   │   └── stm32f429xx.sct
│   ├── TOOLCHAIN_GCC_ARM
│   │   ├── STM32F429xI.ld
│   │   └── syscalls.c
│   ├── usbh_conf.c
│   ├── usbh_conf.h
│   ├── usbh_diskio_dma.c
│   └── usbh_diskio_dma.h
└── README.md

