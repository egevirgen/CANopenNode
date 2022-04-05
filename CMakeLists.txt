cmake_minimum_required(VERSION 3.5)

project(canopennode LANGUAGES C)


file(GLOB_RECURSE CAN_OPEN_NODE_HEADER "*.h")

#message("CAN_OPEN_NODE_HEADER: ${CAN_OPEN_NODE_HEADER}")

## CANOPEN ##
set(CANOPEN_SRC
    301/CO_ODinterface.c
    301/CO_NMT_Heartbeat.c
    301/CO_HBconsumer.c
    301/CO_Emergency.c
    301/CO_SDOserver.c
    301/CO_SDOclient.c
    301/CO_TIME.c
    301/CO_SYNC.c
    301/CO_PDO.c
    301/crc16-ccitt.c
    301/CO_fifo.c
    303/CO_LEDs.c
    304/CO_GFC.c
    304/CO_SRDO.c
    305/CO_LSSslave.c
    305/CO_LSSmaster.c
    309/CO_gateway_ascii.c
    storage/CO_storage.c
    CANopen.c
    )

include_directories(
    .
    301
    303
    304
    305
    309
    storage
    )

add_definitions("-DCO_SINGLE_THREAD -DCO_MULTIPLE_OD")


add_library(canopennode ${CAN_OPEN_NODE_HEADER} ${CANOPEN_SRC} )

target_include_directories(canopennode PRIVATE ../driver)

