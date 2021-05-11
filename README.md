# Pan Tilt Zoom (PTZ) Controls for OBS Studio

Plugin for OBS Studio to add a PTZ Camera control dock.

![PTZ Controls Screenshot](/doc/ptz-controls-screenshot.png?raw=true "OBS Studio PTZ Controls")

This plugin is a work in progress!
It is not feature complete and not very useful yet.
Feel free to help out!
Patches can be submitted as Github pull requests.

Project build infrastructure based on: https://github.com/obsproject/obs-studio/pull/2380

# Build Instructions

## Build as standalone plugin (recommended for faster build turnaround)

### Standalone Build for Linux

- Install OBS Studio including headers
  - Follow instructions for your distribution: https://obsproject.com/wiki/install-instructions
- clone this repository and build:

```
git clone https://github.com/glikely/obs-ptz
mkdir obs-ptz/build
cd obs-ptz/build
cmake ..
make
```

Copy or symlink ptz-controls.so into the OBS plugins directory.
Typically `/usr/lib/obs-plugins`.

### Standalone Build for Windows

- Build OBS Studio using instructions on OBS-Studio Wiki:
  https://obsproject.com/wiki/Install-Instructions
- Clone this repository into a working directory
- Modify (or copy and modify) `CI\install-script-win.cmd`, changing values of
  `DepsPath`, `QTDIR`, and `LibObs_DIR` to match your local environment
- Create a build directory under obs-ptz
- Run `CI\windows-configure.cmd` to invoke cmake
- Run `CI\windows-build.cmd` to make the binary

```
git clone https://github.com/glikely/obs-ptz
cd obs-ptz
mkdir build
cd build
..\CI\windows-configure.cmd
..\CI\windows-build.cmd
```

- Copy the following files into OBS plugins directory
  - `build\Debug\ptz-controls.dll`
  - `%QTDIR%\bin\Qt5SerialPort.dll`
  - `%QTDIR%\bin\Qt5Gamepadd.dll`

## Build inside OBS source tree

- Build OBS according to official instructions:
  https://obsproject.com/wiki/Install-Instructions
- Check out this repository to UI/frontend-plugins

```
cd obs-studio/UI/frontend-plugins
git clone https://github.com/glikely/obs-ptz
```

- Add obs-ptz to the OBS build scripts using included patch

```
cd obs-studio
git am < UI/frontend-plugins/patches/0001-Add-obs-ptz-plugin-to-OBS-Studio.patch
```

- Rebuild OBS Studio

# Contributing

Contributions welcome!
You can submit changes as GitHub pull requests.
Or email patches to me at mailto:grant.likely@secretlab.ca

See CONTRIBUTING.md for details.
