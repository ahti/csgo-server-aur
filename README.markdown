# csgo-server aur package

This PKGBUILD downloads and packages a CS:GO game server using steamcmd.

## caveats

* run `makepkg` with `PKGEXT=.pkg.tar`, or you will spend hours compressing 13GB of mostly already compressed data
* run the server via the included unit file
* only the `csgo-server` user, created by this package, can run the game server due to permission issues (to be fixed)
