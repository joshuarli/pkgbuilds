# example dockerfile for testing firefox PKGBUILD
# useful for fast cloud computers

FROM archlinux/base

# grep, sudo are required for makepkg
# note: makepkg doesn't require tar, it will fallback to bsdtar
RUN pacman --noconfirm -Syu grep sudo

# makepkg can't be run as root, but requires a sudo-enabled user
RUN useradd --system builder && \
    echo "builder ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

# preinstall depends and makedepends packages for much testing iterations
# uncomment for final dockerfile
RUN pacman --noconfirm -S libpulse gtk3 libxt \
    which make grep python2 python autoconf2.13 pkgconf python \
    clang llvm rust cbindgen python nodejs gtk2 nasm unzip zip yasm gawk m4 diffutils

WORKDIR /build

# prefetch source tarball for faster testing iterations
# uncomment for final dockerfile
RUN pacman --noconfirm -S wget && wget -q "https://archive.mozilla.org/pub/firefox/releases/67.0.2/source/firefox-67.0.2.source.tar.xz"

COPY PKGBUILD .

RUN chown -R builder . && \
    su builder -c 'PKGEXT=".pkg.tar" makepkg -cs --noconfirm'

# RUN pacman -U *.pkg.tar
