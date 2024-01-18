# Building GNUstep Base from source

Other than GNUstep Make, GNUstep Base, which provides FoundationKit, is the most important part of your GNUstep installation, so it's important you configure it correctly. Unlike on Apple systems, CoreFoundation is completely separate from GNUstep Base.

Please also see the [INSTALL](https://github.com/gnustep/libs-base/blob/master/INSTALL) file in the source code repository.

## Configuration and dependencies

If all dependencies are installed on your system, and your dependencies don't have weird bugs in them, then just running `./configure` should be perfectly fine. However, if you're missing dependencies, subtle changes to GNUstep Base will occur, because GNUstep Base tries to compile with reduced features in systems which don't have all of its dependencies.

### Dependencies

#### Highly recommended

* [International Components for Unicode](https://icu.unicode.org/)
  * **Warning:** The lowest version of ICU present on your system must match up with your ICU headers. For example, on Ubuntu 20.04, you must not have `libicu60` present, because `libicu-dev` is for `libicu67`. However, having `libicu66` on your system is fine (at least to my knowledge).
  * Without this library, internationalization and Unicode support will be limited or nonexistent.
  * Required packages on Ubuntu 20.04: `libicu-dev libicu67`
  * [Beyond Linux from Scratch build instructions](https://www.linuxfromscratch.org/blfs/view/svn/general/icu.html)
  * [Official build instructions](https://unicode-org.github.io/icu/userguide/icu4c/build.html)

#### Recommended

* `libcurl` or `libcurl-gnutls`
  * If you need to build `libcurl-gnutls.so` from source, and can't use `libcurl.so` (which is the default SONAME), then follow [these instructions](https://stackoverflow.com/questions/68506099/how-to-build-libcurl-gnutls-so-from-source-code).
  * This is required to use networking classes, like `NSURLSession`.

### `./configure` options

```
`configure' configures this package to adapt to many kinds of systems.

Usage: ./configure [OPTION]... [VAR=VALUE]...

To assign environment variables (e.g., CC, CFLAGS...), specify them as
VAR=VALUE.  See below for descriptions of some of the useful variables.

Defaults for the options are specified in brackets.

Configuration:
  -h, --help              display this help and exit
      --help=short        display options specific to this package
      --help=recursive    display the short help of all the included packages
  -V, --version           display version information and exit
  -q, --quiet, --silent   do not print `checking ...' messages
      --cache-file=FILE   cache test results in FILE [disabled]
  -C, --config-cache      alias for `--cache-file=config.cache'
  -n, --no-create         do not create output files
      --srcdir=DIR        find the sources in DIR [configure dir or `..']

Installation directories:
  --prefix=PREFIX         install architecture-independent files in PREFIX
                          [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
                          [PREFIX]

By default, `make install' will install all the files in
`/usr/local/bin', `/usr/local/lib' etc.  You can specify
an installation prefix other than `/usr/local' using `--prefix',
for instance `--prefix=$HOME'.

For better control, use the options below.

Fine tuning of the installation directories:
  --bindir=DIR            user executables [EPREFIX/bin]
  --sbindir=DIR           system admin executables [EPREFIX/sbin]
  --libexecdir=DIR        program executables [EPREFIX/libexec]
  --sysconfdir=DIR        read-only single-machine data [PREFIX/etc]
  --sharedstatedir=DIR    modifiable architecture-independent data [PREFIX/com]
  --localstatedir=DIR     modifiable single-machine data [PREFIX/var]
  --libdir=DIR            object code libraries [EPREFIX/lib]
  --includedir=DIR        C header files [PREFIX/include]
  --oldincludedir=DIR     C header files for non-gcc [/usr/include]
  --datarootdir=DIR       read-only arch.-independent data root [PREFIX/share]
  --datadir=DIR           read-only architecture-independent data [DATAROOTDIR]
  --infodir=DIR           info documentation [DATAROOTDIR/info]
  --localedir=DIR         locale-dependent data [DATAROOTDIR/locale]
  --mandir=DIR            man documentation [DATAROOTDIR/man]
  --docdir=DIR            documentation root [DATAROOTDIR/doc/PACKAGE]
  --htmldir=DIR           html documentation [DOCDIR]
  --dvidir=DIR            dvi documentation [DOCDIR]
  --pdfdir=DIR            pdf documentation [DOCDIR]
  --psdir=DIR             ps documentation [DOCDIR]

System types:
  --build=BUILD     configure for building on BUILD [guessed]
  --host=HOST       cross-compile to build programs to run on HOST [BUILD]
  --target=TARGET   configure for building compilers for TARGET [HOST]

Optional Features:
  --disable-option-checking  ignore unrecognized --enable/--with options
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --disable-environment-config-file
                                Disables the use of the GNUSTEP_CONFIG_FILE
                                environment variable to specify/override
                                the location of the GNUstep config file
                                at runtime.  This option is occasionally
                                useful to disable the environment variable
                                for sites which wish to 'lock down' users
                                to always work with a specific system-wide
                                configuration.  On unix-like systems the
                                default is for this option to be enabled.
                                It is disabled by default on windows systems
                                so that the base library will not use a
                                config file intended for the gnustep-make
                                system (and containing unix-style paths
                                which cannot be used by windows apps).
                                Normally this should be left at its default
                                setting.
  --disable-importing-config-file
                                Disable importing of an existing GNUstep config
                                file and use inbuilt defaults instead.
  --disable-largefile     omit support for large files
  --enable-nxconstantstring
            Enables the use of the NXConstantString class for old compilers.
  --enable-bfd
        Enables the use of libbfd to provide symbolic stack traces.
        Enabling this option provides support for symbolic stack traces
        on platforms where the backtrace_symbols() function is not
        available or does not work properly.
        Enabling this option also has the effect of changing the license
        of gnustep-base from LGPL to GPL since libbfd uses the GPL license
  --enable-procfs               Use /proc filesystem (default)
  --enable-procfs-psinfo         Use /proc/%pid% to get info
  --enable-pass-arguments       Force user main call to NSProcessInfo initialize
  --enable-fake-main            Force redefine of user main function
  --disable-libffi              Disable use of libffi library
  --enable-ffcall               Enable use of the deprecated ffcall library
  --disable-invocations         Build even if invocation-dependencies are not met
  --disable-iconv               Build even if iconv is not available
  --enable-stricticonv          Build even if iconv is strict
  --disable-xml                 Build even if XML-dependencies are not met
  --disable-xmltest             Do not try to compile and run a test XML program
  --disable-xslt                Build even if XSLT-dependency is not met
  --disable-tls                 Disable use of GNUTLS
  --disable-tlstest             Do not try to compile and run a test TLS program
  --disable-zeroconf            Disable NSNetServices support
  --disable-icu                 Disable International Components for Unicode
  --disable-libdispatch         Disable dispatching blocks via libdispatch
  --disable-nsurlsession                Disable support for NSURLSession

  --enable-setuid-gdomap        Enable installing gdomap as a setuid
                                executable.  By default, it is installed
                                as a normal program intended to be started
                                by root at system boot time, but it can
                                also be started up automatically
                                by any user at any time.  Use this
                                option if you are happy having the program
                                started automatically on demand.


Optional Packages:
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --with-cross-compilation-info=PATH
                                Specify path to the configuration file that
                                contains information for the configure script in
                                case of cross compilation. This information
                                replaces those obtained from running programmes
                                during the configuration phase.
  --with-config-file=PATH       Specify path to the GNUstep config file.
                                This is the location to be used by the base
                                library to locate path information at
                                application or tool runtime.
                                This file might not even exist now; it is
                                not read at configure time.  The base library
                                will only read it at runtime.
                                If unspecified, this uses the same value as
                                the GNUstep make package on unix-like systems,
                                but uses ./GNUstep.conf on mingw so that
                                it is relative to the location of the
                                base library DLL.
                                If a leading './' is specified, the path
                                is taken to be relative to the base library
                                linked runtime, not all operating systems
                                can support this, so on some platforms you
                                may need to specify the location of the
                                config file using the GNUSTEP_CONFIG_FILE
                                environment variable at runtime.
                                If a trailing '/' is specified, the path is
                                used for locating domains but no GNUstep
                                config file is read at runtime.
  --with-default-config=PATH   Specify path to a GNUstep config file to be
                                imported at configure time (now) and used to
                                provide default values for the base library
                                to use at runtime if no GNUstep config file
                                is found at runtime.  If this is not specified
                                then the path from the gnustep-make package
                                is used.
  --with-installation-domain=DOMAIN
                                Specify the domain (SYSTEM, LOCAL,
                                NETWORK or USER) into which
                                gnustep-base will be installed.
                                Whenever relative paths are hardcoded
                                into gnustep-base (at the moment, this
                                happens only on MinGW) this option
                                must be used and must match the domain
                                where you will be installing
                                gnustep-base.
                                If this is not specified, the output of
                                gnustep-config --installation-domain-for=gnustep-base
                                (which should normally be LOCAL) is used.
  --without-unwind        Ignore unwind if found and disable it
  --with-include-flags=FLAGS    Specify all include flags at once
  --with-library-flags=FLAGS    Specify all library flags at once
  --with-ffi-include=PATH       Include path for ffi headers
  --with-ffi-library=PATH       Library path for ffi libs
  --with-libiconv-library=PATH  Library path for libiconv libraries
  --with-xml-prefix=PFX    Prefix where libxml is installed (optional)
  --with-tls-prefix=PFX    Prefix where libgnutls is installed (optional)
  --with-zeroconf-api=API  force use of a specific zeroconf API (mdns or avahi)
  --with-dispatch-include=PATH       Include path for dispatch header
  --with-dispatch-library=PATH       Library path for dispatch lib
  --with-curl=<DIR>       use curl installed in directory <DIR>
  --with-gmp-include=PATH  include path for gmp headers
  --with-gmp-library=PATH  library path for gmp libraries
  --with-gdomap-port=PORT  alternative port for gdomap

Some influential environment variables:
  CC          C compiler command
  CFLAGS      C compiler flags
  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
              nonstandard directory <lib dir>
  LIBS        libraries to pass to the linker, e.g. -l<library>
  CPPFLAGS    (Objective) C/C++ preprocessor flags, e.g. -I<include dir> if
              you have headers in a nonstandard directory <include dir>
  CPP         C preprocessor
  PKG_CONFIG  path to pkg-config utility
  PKG_CONFIG_PATH
              directories to add to pkg-config's search path
  PKG_CONFIG_LIBDIR
              path overriding pkg-config's built-in search path
  XML_CFLAGS  C compiler flags for XML, overriding pkg-config
  XML_LIBS    linker flags for XML, overriding pkg-config
  ICU_CFLAGS  C compiler flags for ICU, overriding pkg-config
  ICU_LIBS    linker flags for ICU, overriding pkg-config

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.

Report bugs to the package provider.
```