Sipcalc is an "advanced" console based ip subnet calculator.

** NOTE **
Sipcalc is not really under active development, but if problems are
encountered I will do what I can to fix them and put out a new release.

Sipcalc was created in 2001, it has the features I want in an ip calculator.
**

Features include:
- IPv4
  * Multiple address and netmask input formats.
  * Retrieving of address information from interfaces.
  * Classfull and CIDR output.
  * Multiple address and netmask output formats (dotted quad, hex, number
    of bits).
  * Output of broadcast address, network class, Cisco wildcard, hosts/range,
    network range.
  * Output of multiple types of bitmaps.
  * Output of a userdefined number of extra networks.
  * Multiple networks input from commandline.
  * Parsing of a newline seperated list of networks from standard input (STDIN).
  * The ability to "split" a network based on a smaller netmask, now also with
    recursive runs on the generated subnets.
  * DNS resolution.
- IPv6
  * Compressed and expanded input addresses.
  * Compressed and expanded output.
  * Standard IPv6 network output.
  * v4 in v6 output.
  * Reverse dns address generation.
  * The ability to "split" a network based on a smaller netmask, now also with
    recursive runs on the generated subnets.
  * DNS resolution.

Sipcalc has been tested on the following platforms.
  * OpenBSD 3.0 (i386)
  * OpenBSD 2.8 (i386)
  * FreeBSD 4.3 (i386)
  * Compaq Tru64 UNIX V5.0A (Alpha)
  * Compaq Tru64 UNIX V5.1 (Alpha)
  * Debian GNU/Linux 2.2 (Linux kernel 2.2.x) (i386)
  * Debian GNU/Linux 2.4(?) (Linux kernel 2.4.x) (i386)
  * Debian GNU/Linux 2.2 (Linux kernel 2.2.x) (Alpha)
  * Debian GNU/Linux 2.2 (Linux kernel 2.2.x) (Sparc - Ultra60)
  * Sun Solaris (8) (Sparc - R220)

See doc/sipcalc.txt for a complete description of sipcalc commandline-version
arguments.
