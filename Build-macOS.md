# Build EDK II on macOS

First of all, run `source envsetup.sh` to add some utilities.

## Most packages

Run:

```
build XXXXPkg/XXXXPkg.dsc
```

## Emulator Package

In `EmulatorPkg/` folder, there is a script named `build.sh`, run it.

There could some errors associated with X11 stuff. Here are the solutions.

# FAQ

X11 package is needed, you can install it through `brew install x11`:

- on Intel Mac, it will be linked under `/usr/local/include` and `/usr/local/lib`;
- on Apple Silicon Mac, it can be located in `/opt/homebrew/include` and `/opt/homebrew/lib`.

There is a hack in the codebase: `EmulatorPkg/Unix/Host/X11IncludeHack`. It is actually a soft link to `/opt/X11/include`, which might be used by some developers for X11 include files. It may not be your X11 path. To cope with that, you can create a soft link for the X11 folder installed by HomeBrew, e.g. for my case: `sudo ln -s /usr/local/Cellar/libx11/1.7.0/ /opt/X11/`. Every thing should go well.
