# N1x NVIDIA

## Setup

### Tools
TDB

### Setup env
```bash
# setup virtail env for python
python -m venv .venv
.venv\Scripts\activate.bat
# (.venv) C:\Users\A78501\n1x_nv>

# Install west
pip install west

# Get codebase
west init -l nvec_mec172x
west update

# export zephyr
west zephyr-export

# Install package
pip install -r ecfwwork\zephyr_fork\scripts\requirements.txt 

```


### Apply patch
```bash
cd ecfwwork/zephyr_fork  

git am ../../nvec_mec172x/zephyr_patches/patches_v3_2.patch
```

## Build
```bash
.venv\Scripts\activate.bat

set ZES_ENABLE_SYSMAN=1
set ZEPHYR_SDK_INSTALL_DIR=C:\Users\Andy\Desktop\app_mplab\zephyr-sdk-0.17.0
set MEC172X_SPI_GEN=C:\Users\Andy\Desktop\I3C\CPGZephyrDocs\MEC172x\SPI_image_gen\mec172x_spi_gen_win.exe
# set PROG_TOOL_PATH="C:\Program Files (x86)\DediProg\SF Programmer"
set PATH=%PATH%;C:\Program Files (x86)\DediProg\SF Programmer

ecfwwork\zephyr_fork\zephyr-env.cmd

cd nvec_mec172x
west build -c -p always -b mec1723_n1x -- -DOVERLAY_CONFIG=debug.conf
west build -b mec1723_n1x -- -DOVERLAY_CONFIG=debug.conf

```

## Flash
```bash

python ..\tools\spi_image_trim_out\generating_binaries.py build\zephyr\spi_image.bin
DpCmd.exe -d
DpCmd.exe -uprimary_image.bin -a 0x4000 -l 0x7E000

# DpCmd.exe -uprimary_image_test_v3.12.bin -a 0x4000 -l 0x7E000

```
