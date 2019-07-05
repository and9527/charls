
<img src="https://raw.githubusercontent.com/team-charls/charls/master/doc/jpeg_ls_logo.png" alt="JPEG-LS Logo" width="100"/>

# CharLS

[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://raw.githubusercontent.com/team-charls/charls/master/LICENSE.md)
[![Build status](https://ci.appveyor.com/api/projects/status/yq0naf3v2m8nfa8r/branch/master?svg=true)](https://ci.appveyor.com/project/vbaderks/charls/branch/master)
[![Build Status](https://travis-ci.org/team-charls/charls.svg?branch=master)](https://travis-ci.org/team-charls/charls)
[![Vcpkg package](https://repology.org/badge/version-for-repo/vcpkg/charls.svg)](https://repology.org/metapackage/charls)

CharLS is a C++ implementation of the JPEG-LS standard for lossless and near-lossless image compression and decompression.
JPEG-LS is a low-complexity image compression standard that matches JPEG 2000 compression ratios.

## Features

* C++14 library implementation with a binary C interface for maximum interoperability.
* Supports Windows, Linux and Solaris in 32 bit and 64 bit.
* Includes an adapter assembly for .NET based languages.
* Excellent compression and decompression performance.

## About JPEG-LS

JPEG-LS (ISO/IEC 14495-1:1999 / ITU-T.87) is an image compression standard derived from the Hewlett Packard LOCO algorithm. JPEG-LS has low complexity (meaning fast compression) and high compression ratios, similar to the JPEG 2000 lossless ratios. JPEG-LS is more similar to the old Lossless JPEG than to JPEG 2000, but interestingly the two different techniques result in vastly different performance characteristics.
Wikipedia on lossless JPEG and JPEG-LS: <http://en.wikipedia.org/wiki/Lossless_JPEG>
Tip: the ITU makes their version of the JPEG-LS standard (ITU-T.87) freely available for download, the text is identical with the ISO version.

## About this software

This project's goal is to provide a full implementation of the ISO/IEC 14495-1:1999, "Lossless and near-lossless compression of continuous-tone still images: Baseline" standard. This library is written from scratch in portable C++. The master branch uses modern C++14. The 1.x branch is maintained in C++03. All mainstream JPEG-LS features are implemented by this library.
According to preliminary test results published on http://imagecompression.info/gralic, CharLS is about *twice as fast* as the original HP code, and beats both JPEG-XR and JPEG 2000 by a factor 3.

### Limitations

* No support for (optional) JPEG restart markers (RST). These markers are rarely used in practice.
* No support for the SPIFF file header.
* No support for oversize image dimension. Maximum supported image dimensions are [1, 65535] by [1, 65535].
* After releasing the original baseline JPEG-LS standard 14495-1:1999, ISO released an extension to the JPEG-LS standard called ISO/IEC 14495-2:2003: "Lossless and near-lossless compression of continuous-tone still images: Extensions". Currently CharLS doesn't support these extensions.

## Supported platforms

The code is regularly compiled/tested on Windows and 64 bit Linux. Additionally, the code has been successfully tested on Linux Intel/AMD 32/64 bit (slackware, debian, gentoo), Solaris SPARC systems, Intel based Macs and Windows CE (ARM CPU, emulated), where the less common compilers may require minor code edits. It leverages C++ language features (templates, traits) to create optimized code, which generally perform best with recent compilers. If you compile with GCC, 64 bit code performs substantially better.

## Getting Started

With [vcpkg](https://github.com/Microsoft/vcpkg) on Windows

```powershell
PS> vcpkg install charls charls:x64-windows
```

For other platforms, install options, how to build from source, and more, take a look at the [Documentation](https://github.com/team-charls/charls/wiki).

Once you have the library, the sample folder provides some code samples to get you started.

## Release Management

This repository is provided as source code, and specifically does not offer binary releases. Instead, it is encouraged to either “live at head” (build from the latest version of or, if necessary, build against a known, supported branch, known as a Long Term Support (LTS) branch.
Support for older compiler versions will be phased out, 5 years from the moment that a newer version of that compiler has become available. The same applies to the minimal required C++ language version.

### Long Term Support (LTS) Branches

Before any major breaking change in the API and/or ABI a branch will be created from master to freeze that snapshot as LTS branch.

## Users & Acknowledgements

CharLS is being used by [GDCM DICOM toolkit](http://sourceforge.net/projects/gdcm/), thanks for [Mathieu Malaterre](http://sourceforge.net/users/malat) for getting CharLS started on Linux. [Kato Kanryu](http://knivez.homelinux.org/) wrote an initial version of the color transfroms and the DIB output format code, for an [irfanview](http://www.irfanview.com) plugin using CharLS. Thanks to Uli Schlachter, CharLS now finally runs correctly on big-endian architectures like Sun SPARC.

## Legal

The code in this project is available through a BSD style license, allowing use of the code in commercial closed source applications if you wish. **All** the code in this project is written from scratch, and not based on other JPEG-LS implementations. Be aware that Hewlett Packard claims to own patents that apply to JPEG-LS implementations, but they license it for free for conformant JPEG-LS implementations. Some of these patents may already have expired in your country. Read more at <http://www.hpl.hp.com/loco/> before you use this if you use this code for commercial purposes.
