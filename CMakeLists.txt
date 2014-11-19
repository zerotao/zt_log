cmake_minimum_required(VERSION 2.8.12)
# cmake_policy(SET CMP0042 NEW) # use rpath by default on OSX

set(CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake)

set(PACKAGE "zt_log")
set(PACKAGE_MAJOR_VERSION 0)
set(PACKAGE_MINOR_VERSION 1)
set(PACKAGE_PATCH_VERSION 0)
set(PACKAGE_VERSION ${PACKAGE_MAJOR_VERSION}.${PACKAGE_MINOR_VERSION}.${PACKAGE_PATCH_VERSION})
set(PACKAGE_NAME ${PACKAGE}-${PACKAGE_VERSION})
set(PACKAGE_BUGREPORT "jshiffer@zerotao.org")

set(BUILD_SHARED_LIBS ON)

include(CheckDefIncludeFiles)

check_def_include_files(stdint.h HAVE_STDINT_H)
check_def_include_files(string.h HAVE_STRING_H)
check_def_include_files(strings.h HAVE_STRINGS_H)
# check_def_include_files(inttypes.h HAVE_INTTYPES_H)
# check_def_include_files(stdio.h HAVE_STDIO_H)
# check_def_include_files(stdlib.h HAVE_STDLIB_H)
# check_def_include_files(limits.h HAVE_LIMITS_H)
# check_def_include_files(errno.h HAVE_ERRNO_H)
check_def_include_files(stdio.h HAVE_STDIO_H)
check_def_include_files(stdarg.h HAVE_STDARG_H)
check_def_include_files(unistd.h HAVE_UNISTD_H)
check_def_include_files(syslog.h HAVE_SYSLOG_H)
check_def_include_files(pthread.h HAVE_PTHREAD_H)


###########################################
# Setup and build the sources
#
include_directories(${CMAKE_SOURCE_DIR}/src
                    ${CMAKE_BINARY_DIR}/src)
add_subdirectory(src)
add_subdirectory(examples)
