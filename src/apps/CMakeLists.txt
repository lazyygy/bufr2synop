INCLUDE_DIRECTORIES( ${bufr2synop_SOURCE_DIR}/src/bufrdeco ${bufr2synop_SOURCE_DIR}/src/libraries 
                     ${bufr2synop_SOURCE_DIR} $(all_includes) )

LINK_DIRECTORIES( ${bufr2synop_SOURCE_DIR}/src/bufrdeco ${bufr2synop_SOURCE_DIR}/src/libraries 
                    /usr/lib /usr/lib64 /usr/local/lib /usr/local/lib64)

add_executable(bufr2synop bufr2synop.c bufr2synop_io.c)
target_link_libraries(bufr2synop bufr2tac bufr m gfortran)

add_executable(bufr_decode bufr_decode.c)
target_link_libraries(bufr_decode bufr m gfortran)

add_executable(bufrnoaa bufrnoaa.c bufrnoaa_io.c bufrnoaa_utils.c)

add_executable(bufrdeco_test bufrdeco_test.c)
target_link_libraries(bufrdeco_test m bufrdeco)

add_executable(bufrtotac bufrtotac.c bufrtotac_io.c)
target_link_libraries(bufrtotac m bufrdeco bufr2tac)

add_executable(build_bufrdeco_tables build_bufrdeco_tables.c)
target_link_libraries(build_bufrdeco_tables m bufrdeco)

add_executable(update_tableD update_tableD.c)
target_link_libraries(update_tableD m bufrdeco)
