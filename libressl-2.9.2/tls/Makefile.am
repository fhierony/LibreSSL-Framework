include $(top_srcdir)/Makefile.am.common

lib_LTLIBRARIES = libtls.la

EXTRA_DIST = VERSION
EXTRA_DIST += CMakeLists.txt
EXTRA_DIST += tls.sym

libtls_la_LDFLAGS = -version-info @LIBTLS_VERSION@ -no-undefined -export-symbols $(top_srcdir)/tls/tls.sym
libtls_la_LIBADD = $(abs_top_builddir)/ssl/libssl.la
libtls_la_LIBADD += $(abs_top_builddir)/crypto/libcrypto.la
libtls_la_LIBADD += $(PLATFORM_LDADD)

libtls_la_CPPFLAGS = $(AM_CPPFLAGS)
if OPENSSLDIR_DEFINED
libtls_la_CPPFLAGS += -D_PATH_SSL_CA_FILE=\"@OPENSSLDIR@/cert.pem\"
else
libtls_la_CPPFLAGS += -D_PATH_SSL_CA_FILE=\"$(sysconfdir)/ssl/cert.pem\"
endif

libtls_la_SOURCES = tls.c
libtls_la_SOURCES += tls_client.c
libtls_la_SOURCES += tls_bio_cb.c
libtls_la_SOURCES += tls_config.c
libtls_la_SOURCES += tls_conninfo.c
libtls_la_SOURCES += tls_keypair.c
libtls_la_SOURCES += tls_server.c
libtls_la_SOURCES += tls_ocsp.c
libtls_la_SOURCES += tls_peer.c
libtls_la_SOURCES += tls_util.c
libtls_la_SOURCES += tls_verify.c
noinst_HEADERS = tls_internal.h

if HOST_WIN
libtls_la_SOURCES += compat/ftruncate.c
libtls_la_SOURCES += compat/pread.c
libtls_la_SOURCES += compat/pwrite.c
endif
