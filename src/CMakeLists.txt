set(ZT_LOG_SRCS
    zt_log.c
    zt_log/log_file.c zt_log/log_private.c
    zt_log/log_stderr.c zt_log/log_syslog.c
)

set(ZT_LOG_HDRS
    zt_log.h
    zt_log/log_file.h zt_log/log_interface.h
    zt_log/log_private.h zt_log/log_stderr.h
    zt_log/log_syslog.h
)

add_library(zt_log ${ZT_LOG_SRCS} ${ZT_LOG_HDRS})

set(log_INSTALL_HEADERS ${ZT_LOG_HDRS})
set(log_INSTALL_TARGETS zt_log)

if (WIN32)
    if(CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
        set(CMAKE_INSTALL_PREFIX "${PROJECT_BINARY_DIR}/install" CACHE PATH "Windows install prefix" FORCE)
    endif(CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)

    if (CMAKE_SIZEOF_VOID_P EQUAL 8)
        set(EXECUTABLE_OUTPUT_PATH ${EXECUTABLE_OUTPUT_PATH}/x64)
    endif()
endif(WIN32)

install(TARGETS ${log_INSTALL_TARGETS}
        ARCHIVE DESTINATION lib
        LIBRARY DESTINATION lib)

install(FILES ${LOG_INSTALL_HEADERS} DESTINATION include)
