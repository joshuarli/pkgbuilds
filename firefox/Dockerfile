# example dockerfile for testing firefox PKGBUILD
# useful for fast cloud computers

FROM archlinux/base

# grep, sudo are required for makepkg
# note: makepkg doesn't require tar, it will fallback to bsdtar
RUN pacman --noconfirm -Syu grep sudo

# makepkg can't be run as root, but requires a sudo-enabled user
RUN useradd --system --create-home builder && \
    echo "builder ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

USER builder
WORKDIR /home/builder/build
COPY PKGBUILD .
RUN sudo chown -R builder:builder .

# preinstall depends and makedepends packages for faster testing iterations
# comment out in final dockerfile
#RUN sudo pacman --noconfirm -S libpulse gtk3 libxt \
#    which make grep python2 python autoconf2.13 pkgconf python \
#    clang llvm rust cbindgen python nodejs gtk2 nasm unzip zip yasm gawk m4 diffutils

# prefetch and extract source tarball for faster testing iterations
# comment out in final dockerfile
#RUN sudo pacman --noconfirm -S wget && \
#    wget -q "https://archive.mozilla.org/pub/firefox/releases/67.0.2/source/firefox-67.0.2.source.tar.xz" -O - | \
#    tar xJf -

# testing only; comment out in final dockerfile
#COPY mozconfig firefox-67.0.2/

# XXX: mach needs this
ENV SHELL=/bin/bash

RUN PKGEXT=".pkg.tar" makepkg -cs --noconfirm

RUN sudo pacman -U *.pkg.tar
