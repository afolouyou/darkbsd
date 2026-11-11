DarkBSD
========

DarkBSD is a free, fast, secure, and highly portable Unix-like Open
Source operating system derived from NetBSD.  It keeps the NetBSD
kernel and userland, but reduces the supported hardware set and
replaces the package management stack with XBPS.  The result is a
smaller, more focused system intended for desktop use, with server use
as a secondary goal.

Supported Platforms
-------------------

DarkBSD currently targets:

- amd64 (x86_64)
- arm64 / aarch64 (evbarm)

Support for riscv is under preparation and should be considered
experimental.

The supported platform list is intentionally small.  This keeps the
build and test matrix manageable and allows the system to be tuned for
the remaining platforms.

Package Management
------------------

DarkBSD uses XBPS as its binary package manager.  The XBPS runtime
tools are built natively with the NetBSD build system.  The legacy
pkg_install and pkgin front ends are being retired.

Building
--------

You can cross-build DarkBSD from most UNIX-like operating systems.
To build for amd64 (x86_64), in the source directory:

    ./build.sh -U -u -j4 -m amd64 -O ~/obj \
        -V BUILD_tests=no -V BUILD_games=no build

To build for arm64 (evbarm/aarch64):

    ./build.sh -U -u -j4 -m evbarm -a aarch64 -O ~/obj \
        -V BUILD_tests=no -V BUILD_games=no build

The `build` target produces a complete build tree.  The `release`
target produces installation sets and media.  Pass the same `-V`
options to keep tests and games disabled.  Additional build
information is available in the [BUILDING](BUILDING) file.

Releases
--------

There are no official DarkBSD releases yet.  The source tree is the
primary distribution.

Testing
-------

On a running DarkBSD system:

    cd /usr/tests; atf-run | atf-report

The test suite is inherited from NetBSD.  It is not included in the
example build commands above; enable it with `-V BUILD_tests=yes` when
needed.

Troubleshooting
---------------

- Report bugs and patches via the [GitHub issue tracker](https://github.com/afolouyou/darkbsd/issues).
- For NetBSD-specific questions, the upstream [NetBSD documentation](https://www.NetBSD.org/docs/) and mailing lists may still be useful.

Latest Sources
--------------

To clone the DarkBSD source tree:

    git clone https://github.com/afolouyou/darkbsd.git

DarkBSD tracks NetBSD-current.  The upstream NetBSD source tree is
available at:

    git clone https://github.com/NetBSD/src.git

Additional Links
----------------

- [The NetBSD Guide](https://www.NetBSD.org/docs/guide/en/)
- [NetBSD manual pages](https://man.NetBSD.org/)
- [NetBSD Cross-Reference](https://nxr.NetBSD.org/)
- [XBPS package manager](https://github.com/void-linux/xbps)
