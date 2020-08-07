include $(top_srcdir)/Makefile.tool.am

#----------------------------------------------------------------------------
# Headers
#----------------------------------------------------------------------------

pkginclude_HEADERS = \
	taintfuzz.h

bin_SCRIPTS = \
        taintfuzz

noinst_HEADERS = \
	tnt_include.h \
	tnt_strings.h \
        copy.h

#----------------------------------------------------------------------------
# taintfuzz-<platform>
#----------------------------------------------------------------------------

noinst_PROGRAMS  = taintfuzz-@VGCONF_ARCH_PRI@-@VGCONF_OS@
if VGCONF_HAVE_PLATFORM_SEC
noinst_PROGRAMS += taintfuzz-@VGCONF_ARCH_SEC@-@VGCONF_OS@
endif

TAINTGRIND_SOURCES_COMMON = \
	tnt_syswrap.c \
	tnt_main.c \
	tnt_translate.c \
        copy.c \
        tnt_smt2.c

taintfuzz_@VGCONF_ARCH_PRI@_@VGCONF_OS@_SOURCES      = $(TAINTGRIND_SOURCES_COMMON)
taintfuzz_@VGCONF_ARCH_PRI@_@VGCONF_OS@_CPPFLAGS     = \
	$(AM_CPPFLAGS_@VGCONF_PLATFORM_PRI_CAPS@)
taintfuzz_@VGCONF_ARCH_PRI@_@VGCONF_OS@_CFLAGS       = \
	$(AM_CFLAGS_@VGCONF_PLATFORM_PRI_CAPS@) -O2
taintfuzz_@VGCONF_ARCH_PRI@_@VGCONF_OS@_DEPENDENCIES = \
	$(TOOL_DEPENDENCIES_@VGCONF_PLATFORM_PRI_CAPS@)
taintfuzz_@VGCONF_ARCH_PRI@_@VGCONF_OS@_LDADD        = \
	$(TOOL_LDADD_@VGCONF_PLATFORM_PRI_CAPS@)
taintfuzz_@VGCONF_ARCH_PRI@_@VGCONF_OS@_LDFLAGS      = \
	$(TOOL_LDFLAGS_@VGCONF_PLATFORM_PRI_CAPS@)
taintfuzz_@VGCONF_ARCH_PRI@_@VGCONF_OS@_LINK = \
        ../coregrind/link_tool_exe_@VGCONF_OS@ \
        @VALT_LOAD_ADDRESS_PRI@ \
        $(LINK) \
        $(taintfuzz_@VGCONF_ARCH_PRI@_@VGCONF_OS@_CFLAGS) \
        $(taintfuzz_@VGCONF_ARCH_PRI@_@VGCONF_OS@_LDFLAGS)

if VGCONF_HAVE_PLATFORM_SEC
taintfuzz_@VGCONF_ARCH_SEC@_@VGCONF_OS@_SOURCES      = $(TAINTGRIND_SOURCES_COMMON)
taintfuzz_@VGCONF_ARCH_SEC@_@VGCONF_OS@_CPPFLAGS     = \
	$(AM_CPPFLAGS_@VGCONF_PLATFORM_SEC_CAPS@)
taintfuzz_@VGCONF_ARCH_SEC@_@VGCONF_OS@_CFLAGS       = \
	$(AM_CFLAGS_@VGCONF_PLATFORM_SEC_CAPS@) -O2
taintfuzz_@VGCONF_ARCH_SEC@_@VGCONF_OS@_DEPENDENCIES = \
	$(TOOL_DEPENDENCIES_@VGCONF_PLATFORM_SEC_CAPS@)
taintfuzz_@VGCONF_ARCH_SEC@_@VGCONF_OS@_LDADD        = \
	$(TOOL_LDADD_@VGCONF_PLATFORM_SEC_CAPS@)
taintfuzz_@VGCONF_ARCH_SEC@_@VGCONF_OS@_LDFLAGS      = \
	$(TOOL_LDFLAGS_@VGCONF_PLATFORM_SEC_CAPS@)
taintfuzz_@VGCONF_ARCH_SEC@_@VGCONF_OS@_LINK = \
        ../coregrind/link_tool_exe_@VGCONF_OS@ \
        @VALT_LOAD_ADDRESS_SEC@ \
        $(LINK) \
        $(taintfuzz_@VGCONF_ARCH_SEC@_@VGCONF_OS@_CFLAGS) \
        $(taintfuzz_@VGCONF_ARCH_SEC@_@VGCONF_OS@_LDFLAGS)
endif

tnt_main.o: CFLAGS += -fomit-frame-pointer

