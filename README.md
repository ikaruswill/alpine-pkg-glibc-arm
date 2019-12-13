# arm-alpine-pkg-glibc

[![Build Status](https://drone.ikaruswill.com/api/badges/ikaruswill/arm-alpine-pkg-glibc/status.svg)](https://drone.ikaruswill.com/ikaruswill/arm-alpine-pkg-glibc) ![x86_64](https://img.shields.io/badge/armv7l-supported-brightgreen.svg)

This is the [GNU C Library](https://gnu.org/software/libc/) as a Alpine Linux package for `armv7l` to run binaries linked against `glibc`. This package utilizes a custom built glibc binary based on the vanilla glibc source. Built binary artifacts come from https://github.com/ikaruswill/arm-docker-glibc-builder.

## Releases

See the [releases page](https://github.com/sgerrand/alpine-pkg-glibc/releases) for the latest download links. If you are using tools like `localedef` you will need the `glibc-bin` and `glibc-i18n` packages in addition to the `glibc` package.

## Installing

The current installation method for these packages is to pull them in using `wget` or `curl` and install the local file with `apk`:

    apk --no-cache add ca-certificates wget
    wget -q -O /etc/apk/keys/ikaruswill.rsa.pub https://alpine-pkgs.ikaruswill.com/ikaruswill.rsa.pub
    wget https://github.com/ikaruswill/arm-alpine-pkg-glibc/releases/download/2.29-r0/glibc-2.29-r0.apk
    apk add glibc-2.29-r0.apk

## Locales

You will need to generate your locale if you would like to use a specific one for your glibc application. You can do this by installing the `glibc-i18n` package and generating a locale using the `localedef` binary. An example for en_US.UTF-8 would be:

    apk add glibc-bin-2.29-r0.apk glibc-i18n-2.29-r0.apk
    /usr/glibc-compat/bin/localedef -i en_US -f UTF-8 en_US.UTF-8
