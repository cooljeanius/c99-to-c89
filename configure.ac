dnl#                                               -*- Autoconf -*-
dnl# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([c99-to-c89],[GH],[/dev/null])
AC_CONFIG_SRCDIR([compilewrap.c])
AC_CONFIG_HEADER([config.h])
AC_CONFIG_MACRO_DIR([m4])
AC_CANONICAL_TARGET
AC_USE_SYSTEM_EXTENSIONS
AM_INIT_AUTOMAKE([1.7 foreign -Wall])
AM_MAINTAINER_MODE
AC_OBJEXT
AC_EXEEXT

# Checks for programs.
AC_LANG([C])
AC_PROG_CC_C99
AM_PROG_CC_STDC
AC_PROG_GCC_TRADITIONAL
AX_CHECK_GNU_MAKE
EBG_PROG_CLANG([3.1])
AX_LLVM([Core]) dnl#TODO: figure out how to use this macro properly

# Checks for libraries.
# FIXME: Replace `main' with a function in `-lclang':
AC_CHECK_LIB([clang],[main])

# Checks for header files.
AC_CHECK_HEADERS([assert.h clang-c/Index.h ctype.h malloc.h \
                  stdarg.h stdio.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST
AC_C_PROTOTYPES
AC_C_RESTRICT
AC_TYPE_UINT32_T
AC_TYPE_UINT64_T

# Checks for library functions.
AC_FUNC_MALLOC
AC_FUNC_MEMCMP
AC_FUNC_REALLOC
AC_FUNC_STRTOD
AC_CHECK_FUNCS([dprintf fopen fclose fprintf free isascii memmove memset \
                strcmp strcpy strdup strrchr strtol])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
