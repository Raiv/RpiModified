
# raspivid
cmake_minimum_required(VERSION 2.8)

SET(COMPILE_DEFINITIONS -Werror)

include_directories(./)
include_directories(./bcm_host/include)
include_directories(./interface/vcos/pthreads/)
include_directories(./interface/vmcs_host/linux/)



set (COMMON_SOURCES
   RaspiCamControl.c
   RaspiCLI.c
   RaspiPreview.c)

add_executable(raspivid   ${COMMON_SOURCES} RaspiVid.c)

set (MMAL_LIBS mmal_core mmal_util mmal_vc_client)

target_link_libraries(raspivid   ${MMAL_LIBS} vcos bcm_host)

install(TARGETS raspivid RUNTIME DESTINATION bin)
