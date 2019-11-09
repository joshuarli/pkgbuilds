NAME := spacefm

all:
	PKGEXT='.pkg.tar' makepkg -crsi

# package only
.PHONY: pkg
pkg:
	PKGEXT='.pkg.tar' makepkg -crs

clean:
	rm -rf pkg src joshuarli-$(NAME)-*
