# == DO NOT EDIT THE FOLLOWING LINES for the Raspberry Pi Pico VS Code Extension to work ==
if(WIN32)
    set(USERHOME $ENV{USERPROFILE})
else()
    set(USERHOME $ENV{HOME})
endif()
set(sdkVersion 2.2.0)
set(toolchainVersion 14_2_Rel1)
set(picotoolVersion 2.2.0-a4)
set(picoVscode ${USERHOME}/.pico-sdk/cmake/pico-vscode.cmake)
if (EXISTS ${picoVscode})
    include(${picoVscode})
endif()
# ====================================================================================
set(PICO_BOARD pico2 CACHE STRING "Board type")

cmake_minimum_required(VERSION 3.13...3.27)

include(pico_sdk_import.cmake)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(PICO_TINYUSB_PATH ${CMAKE_CURRENT_LIST_DIR}/lib/tinyusb)
project(pico_usb_audio_serial C CXX ASM)
pico_sdk_init()

add_executable(${CMAKE_PROJECT_NAME}
  src/main.c
  src/usb_descriptors.c
  src/led.c
  src/ringbuffer.c
)
target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE ${CMAKE_CURRENT_LIST_DIR}/include)
target_link_libraries(${CMAKE_PROJECT_NAME}
  pico_stdlib
  tinyusb_device
  tinyusb_board
  pico_stdio_usb  # Kényszeríti a CDC (Soros port) hardveres lánc lefutását
)
pico_add_extra_outputs(${CMAKE_PROJECT_NAME})
