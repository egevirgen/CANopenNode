cmake_minimum_required(VERSION 3.5)

project(canopennode LANGUAGES C)


file(GLOB_RECURSE CAN_OPEN_NODE_HEADER "*.h")

#message("CAN_OPEN_NODE_HEADER: ${CAN_OPEN_NODE_HEADER}")

## CANOPEN ##
set(CANOPEN_SRC
    CO_Emergency.c
    CO_HBconsumer.c
    CO_NMT_Heartbeat.c
    CO_PDO.c
    CO_SDO.c
    CO_SDOmaster.c
    CO_SYNC.c
    CO_trace.c
    crc16-ccitt.c
    CANopen.c
    )

include_directories(
    .
    )

add_definitions("-DCO_SINGLE_THREAD -DCO_MULTIPLE_OD")


add_library(canopennode ${CAN_OPEN_NODE_HEADER} ${CANOPEN_SRC} )

target_include_directories(canopennode PRIVATE ../driver)

