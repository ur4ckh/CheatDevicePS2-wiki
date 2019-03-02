This will explain how to compile Cheat Device on Linux. This was tested under Fedora 25 x86_64 but should work with other distros.

**1. Install necessary tools for building the toolchain. Some of these are probably installed already.**
 * gcc
 * make
 * autoconf
 * automake
 * patch
 * wget

**2. Install PS2SDK using ps2toolchain**
  ```
git clone https://github.com/ps2dev/ps2toolchain.git ~/ps2toolchain
cd ~/ps2toolchain
sudo ./toolchain-sudo.sh
  ```

**3. Add environment variables to ~/.bashrc**
  ```
export PS2DEV=/usr/local/ps2dev
export PS2SDK=$PS2DEV/ps2sdk
export GSKIT=$PS2DEV/gsKit
export PATH=$PATH:$PS2DEV/bin
export PATH=$PATH:$PS2DEV/ee/bin
export PATH=$PATH:$PS2DEV/iop/bin
export PATH=$PATH:$PS2DEV/dvp/bin
export PATH=$PATH:$PS2SDK/bin
  ```

**4. Give all users write permission for ps2dev directory**
  ```
sudo chmod g+w,o+w -R $PS2DEV
  ```

**5. Install zlib**
  ```
git clone git://github.com/ps2dev/ps2sdk-ports.git ~/ports
cd ~/ports/zlib
make install
  ```

**6. Install gsKit**
  ```
git clone git://github.com/ps2dev/gsKit ~/gsKit
cd ~/gsKit
./setup.sh
  ```
That last step will warn you about not having some image libraries available, but this can be ignored since Cheat Device doesn't need them.

**7. Compile Cheat Device**
  ```
git clone git://github.com/root670/CheatDevicePS2 ~/CheatDevicePS2
cd ~/CheatDevicePS2
make
  ```

# Build Options
These can be passed in as arguments to `make` or the Docker build scripts.
|Argument|Description|
|---|---|
|DTL_T10000=1|Create executable compatible with PS2 TOOL (DTL-T10000)|
|NO_MASS=1|Replace "mass" device names with "host". This helps with debugging the save manager with PCSX2|