NAME := nmap

all:
	PKGEXT='.pkg.tar' makepkg -csi

# package only
pkg:
	PKGEXT='.pkg.tar' makepkg -cs

install:
	sudo pacman -U *.pkg.tar

clean:
	rm -rf pkg src $(NAME)-*
