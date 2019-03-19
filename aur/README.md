example openssh config block

```
Host aur.archlinux.org
    IdentitiesOnly yes
    User aur
    IdentityFile ~/.ssh/joshuarli-aur
```

before editing pkgbuilds, `source devel`:

    - `newpkg [pkgname]` to create a new, empty package 
    - `mksrcinfo` to regenerate `.SRCINFO` every time the `PKGBUILD` is edited
        - `editpkg` to automate this process
    - `mkpkg` then `ipkg` to build and install the `.pkg.tar` for testing
