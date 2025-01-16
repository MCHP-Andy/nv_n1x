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
```
```
