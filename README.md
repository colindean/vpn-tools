PCF conversion tools
====================

This is a collection of tools for converting and extracting information from 
Cisco IPSEC VPN configuration files, commonly with a "pcf" extension. Use these
tools to decrypt the secret, primarily, so that you can use an OS's built-in
VPN clients instead of Cisco's clients that are prone not to working on 
anything but Windows.

The various components are copyright their respective owners, listed en dosier.
This repository is just a personal backup of a set of tools I use more often 
than I would like to admit.

Installation
------------

You'll need to install libgcrypt 1.5.0 or earlier. cisco-decrypt.c uses some
functions that were deprecated in 1.5.0. You can most likely install libgcrypt
through your package manager on Linux or with Ports or Homebrew on OSX (for me,
it's usually just a `brew install libgcrypt` away on a new build).

Compile `cisco-decrypt.c` with this command, assuming you have gcc installed:

    gcc -Wall -o cisco-decrypt cisco-decrypt.c $(libgcrypt-config --libs --cflags)

You'll also need to have Perl installed, but you probably already do.

Use
---

I generally run the command like this:

   ./pcf2vpnc corporate-vpn.pcf > corporate-vpn.vpnc

The output is suitable for using with `vpnc` directly, or you can read it and
configure Network Manager or OSX's built-in client or whatever manually. The 
ID field is the Group, and everything else is pretty self-explanatory.

Contributing
------------

Things to add? Problems? Submit a pull request.
