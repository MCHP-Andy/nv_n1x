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
set ZEPHYR_SDK_INSTALL_DIR=C:\Users\A78501\mchp_zephyr\zephyr-sdk-0.17.0
# Download from: https://github.com/zephyrproject-rtos/sdk-ng/releases/download/v0.17.0/zephyr-sdk-0.17.0_windows-x86_64.7z
set MEC172X_SPI_GEN=C:\Users\A78501\n1x\tools\spi_gen\MEC172x\SPI_image_gen\mec172x_spi_gen_win.exe

ecfwwork\zephyr_fork\zephyr-env.cmd

cd nvec_mec172x 
west build -c -p always -b mec1723_n1x -- -DOVERLAY_CONFIG=debug.conf 

```
