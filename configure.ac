#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

# The maintainer mode is causing me grief with newest versions of autotools
#AM_MAINTAINER_MODE
AC_INIT([backupninja],[1.2.99],[backupninja@lists.riseup.net])
AC_CONFIG_SRCDIR([src/backupninja.in])
AM_INIT_AUTOMAKE([foreign])

# Checks for programs.

AC_PATH_PROGS(BASH, bash, "no", [$PATH:/bin:/usr/bin:/usr/sbin])
if test x$BASH = "xno"; then
    AC_MSG_ERROR([bash is required])
fi

AC_PATH_PROGS(SED, sed, "no")
if test x$SED = "xno"; then
    AC_MSG_ERROR([sed is required])
else
   export SED
fi

AC_PATH_PROGS(AWK, awk, "no")
if test x$AWK = "xno"; then
    AC_MSG_ERROR([awk is required])
else
   export AWK
fi

AC_PATH_PROGS(MKTEMP, mktemp, "no")
if test x$MKTEMPT = "xno"; then
    AC_MSG_ERROR([mktemp is required])
fi

AC_PATH_PROGS(STAT, stat, "no")
if test x$STAT = "xno"; then
    AC_MSG_ERROR([stat is required])
else
   export STAT
fi

AC_CHECK_PROG(ac_cv_have_rpm, rpm, "yes", "no")
if test "x$ac_cv_have_rpm" = "xyes"; then
        rpm --define '_topdir /tmp' > /dev/null 2>&1
        AC_MSG_CHECKING(to see if we can redefine _topdir)
        if test $? -eq 0 ; then
                AC_MSG_RESULT(yes)
                HAVE_RPM=yes
        else
                AC_MSG_RESULT(no.  You'll have to build packages manually.)
                HAVE_RPM=no
        fi
fi
AC_SUBST(HAVE_RPM)

AC_CHECK_PROG(ac_cv_have_rpm, rpm, "yes", "no")
if test "x$ac_cv_have_rpm" = "xyes"; then
        rpm --define '_topdir /tmp' > /dev/null 2>&1
        AC_MSG_CHECKING(to see if we can redefine _topdir)
        if test $? -eq 0 ; then
                AC_MSG_RESULT(yes)
                HAVE_RPM=yes
        else
                AC_MSG_RESULT(no.  You'll have to build packages manually.)
                HAVE_RPM=no
        fi
fi
AC_SUBST(HAVE_RPM)

AC_PROG_LN_S

AC_SUBST([CFGDIR], "${sysconfdir}")

AC_CONFIG_FILES([Makefile
                etc/Makefile
                examples/Makefile
                handlers/Makefile
                lib/Makefile
                man/Makefile
                src/Makefile])

AC_OUTPUT([ backupninja.spec])
