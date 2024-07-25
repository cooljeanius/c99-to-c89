dnl#                                               -*- Autoconf -*-
dnl# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([c99-to-c89],[GH],[/dev/null])
AC_CONFIG_SRCDIR([compilewrap.c])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_AUX_DIR([build-aux])
AC_CANONICAL_TARGET
AC_USE_SYSTEM_EXTENSIONS
AM_INIT_AUTOMAKE([1.7 dejagnu dist-zip foreign -Wall])
AM_MAINTAINER_MODE
AC_OBJEXT
AC_EXEEXT

# Checks for programs.
AC_LANG([C])
AC_PROG_CC_C99
AM_PROG_CC_STDC
AX_CHECK_GNU_MAKE
EBG_PROG_CLANG([3.1])
AX_LLVM([Core]) dnl#TODO: figure out how to use this macro properly

# Checks for libraries.
AC_CHECK_LIB([c],[printf])
AC_CHECK_LIB([clang],[clang_getTokenSpelling])dnl

# Checks for header files.
AC_CHECK_HEADERS([assert.h clang-c/Index.h ctype.h malloc.h malloc/malloc.h \
                  stdarg.h stdio.h])dnl

if test "x${ac_cv_header_inttypes_h}" = "x"; then
  test -z "${ac_cv_header_inttypes_h}" || unset ac_cv_header_inttypes_h
  AC_CHECK_HEADERS([inttypes.h])
fi
if test "x${ac_cv_header_stdint_h}" = "x"; then
  test -z "${ac_cv_header_stdint_h}" || unset ac_cv_header_stdint_h
  AC_CHECK_HEADERS([stdint.h])
fi
if test "x${ac_cv_header_strings_h}" = "x"; then
  test -z "${ac_cv_header_strings_h}" || unset ac_cv_header_strings_h
  AC_CHECK_HEADERS([strings.h])
fi
if test "x${ac_cv_header_unistd_h}" = "x"; then
  test -z "${ac_cv_header_unistd_h}" || unset ac_cv_header_unistd_h
  AC_CHECK_HEADERS([unistd.h])
fi

# Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST
AC_C_PROTOTYPES
AC_C_RESTRICT
AC_TYPE_PID_T
AC_TYPE_UINT32_T
AC_TYPE_UINT64_T

# Checks for library functions.
AC_FUNC_FORK
AC_FUNC_MALLOC
AC_FUNC_MEMCMP
AC_FUNC_REALLOC
AC_FUNC_STRTOD
AC_CHECK_FUNCS([dprintf dup2 fopen fclose fprintf free isascii \
                memmove memset strcmp strcpy strdup strrchr strtol])dnl

# Output.
AC_CONFIG_FILES([Makefile])
AC_OUTPUT
