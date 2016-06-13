#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([TLS extension chainserver], [0.0.1], [willem@nlnetlabs.nl])
AM_INIT_AUTOMAKE([-Wall -Werror])
LT_INIT
AC_CONFIG_SRCDIR([chainserver.c])
AC_CONFIG_HEADERS([config.h])

# Checks for programs.
AC_PROG_CC
AC_PROG_INSTALL

# Checks for libraries.
AC_CHECK_LIB([ssl], [TLS_server_method],[],[AC_MSG_ERROR([OpenSSL >= 1.1.0 is required])])
AC_CHECK_LIB([crypto], [BIO_pop])
AC_CHECK_LIB([event_core], [event_new],[],[AC_MSG_ERROR([libevent >= 2.0.0 is required])])
AC_CHECK_LIB([getdns], [getdns_msg_dict2wire],[],[AC_MSG_ERROR([getdns >= 1.0.0 is required])])
AC_CHECK_LIB([getdns_ext_event], [getdns_extension_set_libevent_base],[],[AC_MSG_ERROR([the libevent extension for getdns is required])])

# Checks for header files.
AC_CHECK_HEADERS([arpa/inet.h inttypes.h netdb.h netinet/in.h stdint.h stdlib.h string.h sys/socket.h unistd.h openssl/ssl.h])
AC_CHECK_DECL([TLS_server_method],[],[AC_MSG_ERROR([OpenSSL >= 1.1.0 is required])],[
	#ifdef HAVE_OPENSSL_SSL_H
	# include <openssl/ssl.h>
	#endif
])

# Checks for typedefs, structures, and compiler characteristics.
AC_TYPE_PID_T
AC_TYPE_SIZE_T
AC_TYPE_SSIZE_T
AC_TYPE_UINT16_T
AC_TYPE_UINT32_T
AC_TYPE_UINT8_T

# Checks for library functions.
AC_FUNC_MALLOC
AC_CHECK_FUNCS([gethostname memset select socket strchr strrchr strstr])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
