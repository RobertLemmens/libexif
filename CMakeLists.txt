cmake_minimum_required(VERSION 3.20)
project(libexif C)

INCLUDE (CheckIncludeFiles)
INCLUDE (CheckFunctionExists)

set (PACKAGE "libexif")
set (PACKAGE_VERSION "0.6.21")
set (PACKAGE_BUGREPORT "libexif-devel@lists.sourceforge.net")
set (PACKAGE_NAME "EXIF library")
set (PACKAGE_STRING "${PACKAGE_NAME} ${PACKAGE_VERSION}")
set (PACKAGE_TARNAME ${PACKAGE})
set (PACKAGE_URL "")

set (GETTEXT_PACKAGE "libexif-12")
set (LOCALEDIR "/usr/local/share/locale")
set (VERSION "${PACKAGE_VERSION}")


# NLS
CHECK_FUNCTION_EXISTS (dcgettext HAVE_DCGETTEXT)
CHECK_INCLUDE_FILES (dlfcn.h HAVE_DLFCN_H)
CHECK_FUNCTION_EXISTS (gettext HAVE_GETTEXT)
CHECK_FUNCTION_EXISTS (iconv HAVE_ICONV)
CHECK_INCLUDE_FILES (inttypes.h HAVE_INTTYPES_H)
CHECK_FUNCTION_EXISTS (localtime_r HAVE_LOCALTIME_R)
CHECK_INCLUDE_FILES (memory.h HAVE_MEMORY_H)
CHECK_INCLUDE_FILES (stdint.h HAVE_STDINT_H)
CHECK_INCLUDE_FILES (stdlib.h HAVE_STDLIB_H)
CHECK_INCLUDE_FILES (strings.h HAVE_STRINGS_H)
CHECK_INCLUDE_FILES ("string.h" HAVE_STRING_H)
CHECK_INCLUDE_FILES ("sys/stat.h" HAVE_SYS_STAT_H)
CHECK_INCLUDE_FILES ("sys/types.h" HAVE_SYS_TYPES_H)
CHECK_INCLUDE_FILES ("unistd.h" HAVE_UNISTD_H)

CONFIGURE_FILE(config.h.cmake ${CMAKE_CURRENT_BINARY_DIR}/config.h)

include_directories(${CMAKE_CURRENT_BINARY_DIR})
include_directories(${CMAKE_CURRENT_SOURCE_DIR})

add_library (
        exif
        libexif/canon/exif-mnote-data-canon.c
        libexif/canon/mnote-canon-entry.c
        libexif/canon/mnote-canon-tag.c
        libexif/exif-byte-order.c
        libexif/exif-content.c
        libexif/exif-data.c
        libexif/exif-entry.c
        libexif/exif-format.c
        libexif/exif-ifd.c
        libexif/exif-loader.c
        libexif/exif-log.c
        libexif/exif-mem.c
        libexif/exif-mnote-data.c
        libexif/exif-tag.c
        libexif/exif-utils.c
        libexif/exif-gps-ifd.c
        libexif/fuji/exif-mnote-data-fuji.c
        libexif/fuji/mnote-fuji-entry.c
        libexif/fuji/mnote-fuji-tag.c
        libexif/olympus/exif-mnote-data-olympus.c
        libexif/olympus/mnote-olympus-entry.c
        libexif/olympus/mnote-olympus-tag.c
        libexif/pentax/exif-mnote-data-pentax.c
        libexif/pentax/mnote-pentax-entry.c
        libexif/pentax/mnote-pentax-tag.c
        libexif/config.h
)
SET_TARGET_PROPERTIES( exif PROPERTIES COMPILE_FLAGS "-fPIC")