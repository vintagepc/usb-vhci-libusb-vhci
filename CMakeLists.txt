#Cmake helper for libusb-vhci
project(libusb-vhci)
cmake_minimum_required(VERSION 2.8.11)
set(LIBUSBVHCI_VERSION 0.8)

set(LIBRARY_NAME usb-vhci)

set(LIBUSB_VHCI_SOURCES
	src/libusb_vhci.c
	src/hcd.cpp
	src/port_stat.cpp
	src/urb.cpp
	src/work.cpp
	src/local_hcd.cpp
)
add_library(${LIBRARY_NAME} STATIC ${LIBUSB_VHCI_SOURCES})
set_target_properties(${LIBRARY_NAME} PROPERTIES VERSION ${LIBUSBVHCI_VERSION})

target_link_libraries(${LIBRARY_NAME} pthread)

target_include_directories(${LIBRARY_NAME} INTERFACE
  src/
  )
