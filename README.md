This project is derived from the `pico-usb-audio-loopback-reverb` repository by Hiroyuki OYAMA. I have removed the reverb function and integrated a serial port. The goal of this project is to serve as a reusable software module for my future projects, such as USB sound cards, SDR (Software Defined Radio), and other implementations.

TinyUSB Dependency

This project requires a specific version of TinyUSB to work correctly. The version bundled with the Pico SDK (e.g. TinyUSB 0.18.0) may not work properly with this project due to differences in the USB Audio implementation.

The project has been tested with the following TinyUSB commit:

12677d4d9b8096cc30c5512f250f356b41409c4a

How to install the required version:

Download the exact version as a ZIP file:
https://github.com/hathach/tinyusb/archive/12677d4d9b8096cc30c5512f250f356b41409c4a.zip
Extract the archive.
Copy the extracted contents into the project's lib/tinyusb/ directory.

Make sure the TinyUSB source files are directly inside lib/tinyusb/, without an extra nested directory.

Important: Use the exact commit above. Other TinyUSB versions may compile successfully but are not guaranteed to work correctly with this project.