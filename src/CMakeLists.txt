set(LOG_SOURCES
    zt_log.c
    zt_log/log_file.c zt_log/log_private.c
    zt_log/log_stderr.c zt_log/log_syslog.c
)

set(LOG_HEADERS
    zt_log.h
)

set(LOG_LOG_HEADERS
    zt_log/log_file.h zt_log/log_interface.h
    zt_log/log_private.h zt_log/log_stderr.h
    zt_log/log_syslog.h
)

add_library(zt_log ${LOG_SOURCES} ${LOG_HEADERS} ${LOG_LOG_HEADERS})


if (WIN32)
    if(CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
        set(CMAKE_INSTALL_PREFIX "${PROJECT_BINARY_DIR}/install" CACHE PATH "Windows install prefix" FORCE)
    endif(CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)

    if (CMAKE_SIZEOF_VOID_P EQUAL 8)
        set(EXECUTABLE_OUTPUT_PATH ${EXECUTABLE_OUTPUT_PATH}/x64)
    endif()
endif(WIN32)

install(TARGETS zt_log
        ARCHIVE DESTINATION lib
        LIBRARY DESTINATION lib)

    install(FILES ${LOG_HEADERS} DESTINATION include)
    install(FILES ${LOG_LOG_HEADERS} DESTINATION include/zt_log)

