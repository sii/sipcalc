AC_INIT(include/sub.h)
AM_CONFIG_HEADER(config.h)
AM_INIT_AUTOMAKE(sipcalc,1.1.6)
AC_PROG_CC
AC_PROG_INSTALL

dnl - Configuration.
AC_HEADER_STDC
AC_CHECK_HEADERS(sys/ioctl.h unistd.h sys/types.h sys/bitypes.h sys/sockio.h netdb.h ctype.h)
AC_PROG_GCC_TRADITIONAL
dnl Solaris also needs libnsl for inet_ntoa and friends.
AC_CHECK_LIB(nsl, inet_ntoa,
[
  AC_DEFINE(HAVE_LIBNSL, 1, libnsl)
  LIBS="$LIBS -lnsl"
])
AC_CHECK_FUNCS(socket strstr strtol strtoul gethostbyname gethostbyname2 inet_ntop getipnodebyaddr getaddrinfo)

dnl - Include /usr/local/include if it exists.
if test -d /usr/local/include;
then
  CFLAGS="${CFLAGS} -I/usr/local/include"
fi

dnl - Include /usr/local/lib if it exists.
if test -d /usr/local/lib;
then
  LIBS="${LIBS} -L/usr/local/lib"
fi


dnl Check if getopt_long is available.

AC_DEFUN([sii_GETOPT_LONG],
[
  AC_CHECK_HEADERS(getopt.h,
  [
    AC_DEFINE(HAVE_GETOPT_H, 1, getopt_h)
  ],
  [
    if test -f /usr/local/include/getopt.h;
    then
      echo checking for getopt.h in /usr/local/include... yes
      AC_DEFINE(HAVE_GETOPT_H, 1, getopt_h)
    fi
  ])
  AC_CHECK_FUNCS(getopt_long,,
  [
    AC_CHECK_LIB(gnugetopt, getopt_long,
    [
      AC_DEFINE(HAVE_GETOPT_LONG, 1, getopt_long)
      LIBS="$LIBS -lgnugetopt"
    ])
  ])
])


dnl Check if we need netdb.h for resolver routines.

AC_DEFUN([sii_GETADDRINFO],
AC_MSG_CHECKING(for getaddrinfo in netdb.h)
AC_TRY_COMPILE(
[
  #include <netdb.h>
],
[struct addrinfo h; struct addrinfo *r; getaddrinfo("127.0.0.1", NULL, &h, &r)],
[
  AC_MSG_RESULT(yes)
  AC_DEFINE(HAVE_GETADDRINFO_NETDB, 1, getaddrinfo_netdb)
],
AC_MSG_RESULT(no)))


AC_DEFUN(sii_GETHOSTBYNAME,
AC_MSG_CHECKING(for gethostbyname in netdb.h)
AC_TRY_COMPILE(
[
  #include <netdb.h>
],
[struct hostent *h; h=gethostbyname("127.0.0.1")],
[
  AC_MSG_RESULT(yes)
  AC_DEFINE(HAVE_GETHOSTBYNAME_NETDB, 1, gethostbyname_netdb)
],
AC_MSG_RESULT(no)))


AC_DEFUN(sii_GETHOSTBYNAME2,
AC_MSG_CHECKING(for gethostbyname2 in netdb.h)
AC_TRY_COMPILE(
[
  #include <netdb.h>
],
[struct hostent *h; h=gethostbyname("127.0.0.1", AF_INET)],
[
  AC_MSG_RESULT(yes)
  AC_DEFINE(HAVE_GETHOSTBYNAME2_NETDB, 1, gethostbyname2_netdb)
],
AC_MSG_RESULT(no)))


dnl Check if struct sockaddr has member sa_len

AC_DEFUN(sii_SA_LEN,
AC_MSG_CHECKING(if struct sockaddr has sa_len field)
AC_TRY_COMPILE(
[
  #include <sys/types.h>
  #include <sys/socket.h>
],
[struct sockaddr sa;int x; x=sizeof(sa.sa_len);],
[
  AC_MSG_RESULT(yes)
  AC_DEFINE(HAVE_SA_LEN, 1, sa_len)
],
AC_MSG_RESULT(no)))


dnl Check if getopt_long is available.

dnl Solaris has socket(2) in libsocket.
AC_DEFUN(sii_LIBSOCKET,
[
  AC_CHECK_LIB(socket, socket,
  [
    AC_DEFINE(HAVE_LIBSOCKET, 1, libsocket)
    LIBS="$LIBS -lsocket"
  ])
])


dnl Check for uint[8,16,32]_t

AC_DEFUN(sii_UINT8_T,
AC_MSG_CHECKING(if type uint8_t exists)
AC_TRY_COMPILE(
[
  #include <sys/types.h>
],
[uint8_t a;],
[
  AC_MSG_RESULT(yes)
  AC_DEFINE(HAVE_UINT8_T, 1, uint8_t)
],
AC_MSG_RESULT(no)))

AC_DEFUN(sii_U_INT8_T,
AC_MSG_CHECKING(if type u_int8_t exists)
AC_TRY_COMPILE(
[
  #include <sys/types.h>
],
[u_int8_t a;],
[
  AC_MSG_RESULT(yes)
  AC_DEFINE(HAVE_U_INT8_T, 1, u_int8_t)
],
AC_MSG_RESULT(no)))



AC_DEFUN(sii_UINT16_T,
AC_MSG_CHECKING(if type uint16_t exists)
AC_TRY_COMPILE(
[
  #include <sys/types.h>
],
[uint16_t a;],
[
  AC_MSG_RESULT(yes)
  AC_DEFINE(HAVE_UINT16_T, 1, uint16_t)
],
AC_MSG_RESULT(no)))

AC_DEFUN(sii_U_INT16_T,
AC_MSG_CHECKING(if type u_int16_t exists)
AC_TRY_COMPILE(
[
  #include <sys/types.h>
],
[u_int32_t a;],
[
  AC_MSG_RESULT(yes)
  AC_DEFINE(HAVE_U_INT16_T, 1, u_int16_t)
],
AC_MSG_RESULT(no)))



AC_DEFUN(sii_UINT32_T,
AC_MSG_CHECKING(if type uint32_t exists)
AC_TRY_COMPILE(
[
  #include <sys/types.h>
],
[uint32_t a;],
[
  AC_MSG_RESULT(yes)
  AC_DEFINE(HAVE_UINT32_T, 1, uint32_t)
],
AC_MSG_RESULT(no)))

AC_DEFUN(sii_U_INT32_T,
AC_MSG_CHECKING(if type u_int32_t exists)
AC_TRY_COMPILE(
[
  #include <sys/types.h>
],
[u_int32_t a;],
[
  AC_MSG_RESULT(yes)
  AC_DEFINE(HAVE_U_INT32_T, 1, u_int32_t)
],
AC_MSG_RESULT(no)))


sii_LIBSOCKET
sii_GETHOSTBYNAME
sii_GETHOSTBYNAME2
sii_GETADDRINFO
sii_SA_LEN
sii_GETOPT_LONG
sii_UINT8_T
sii_UINT16_T
sii_UINT32_T
sii_U_INT8_T
sii_U_INT16_T
sii_U_INT32_T
AC_OUTPUT(Makefile			\
	  doc/Makefile			\
	  include/Makefile		\
	  src/Makefile			\
	 )

