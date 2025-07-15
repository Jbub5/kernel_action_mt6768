# Kernel Build Action for Lancelot & Merlin

This GitHub Action allows you to build a custom Android kernel for the Lancelot and Merlin devices. It provides a wide range of options to customize the build process, including support for KernelSU, APatch, and custom Clang versions.

## Features

- Build custom Android kernels for Lancelot and Merlin devices.
- Support for KernelSU and APatch.
- Option to use custom Clang versions.
- Wide range of customization options.
- Easy to use and configure.

## Step-by-step guide to use

<details>
  <summary><i>Click to open</i></summary>

> ### 1.
> ![01](guide/images/01.png)

> ### 2.
> ![02](guide/images/02.png)
> **Note:** Unselect `Copy the kernel-tree_lancelot branch only` if you are building for merlin.

> ### 3.
> ![03](guide/images/03.png)

> ### 4.
> ![04](guide/images/04.png)

> ### 5.
> ![05](guide/images/05.png)

> ### 6.
> ![06](guide/images/06.png)

> ### 7.
> ![07](guide/images/07.png)

> ### 8.
> ![08](guide/images/08.png)

> ### 9.
> ![09](guide/images/09.png)

> ### 10.
> ![10](guide/images/10.png)

> ### 11.
> ![11](guide/images/11.png)
> **Note:** Reload this page if the yellow circle does not appear.

> ### 12.
> ![12](guide/images/12.png)

> ### 13.
> ![13](guide/images/13.png)

> ### 14.
> ![14](guide/images/14.png)

</details>

## Options Guide

> All options are located in [config.env](config.env)

### Kernel Source

| Option | Description | Default Value |
| --- | --- | --- |
| `KERNEL_SOURCE` | Your kernel repository link. | `https://github.com/Jbub5/android_kernel_xiaomi_mt6768` |
| `KERNEL_SOURCE_BRANCH` | Your kernel branch. | `kernel-tree` |
| `KERNEL_IMAGE_NAME` | The kernel binary that needs to be flashed. | `Image.gz-dtb` |
| `KERNEL_ARCH` | The kernel architecture. | `arm64` |

### KernelSU

| Option | Description | Default Value |
| --- | --- | --- |
| `ENABLE_KERNELSU` | Enable [KernelSU](https://kernelsu.org/guide/what-is-kernelsu.html) support. | `true` |
| `KERNELSU_SETUP_SOURCE` | The source of the KernelSU setup script. | `https://raw.githubusercontent.com/tiann/KernelSU/main/kernel/setup.sh` |
| `KERNELSU_TAG` | Select the branch or tag of KernelSU. | `v1.0.1` |
| `KSU_EXPECTED_SIZE` | Customize the size of the KernelSU manager signature. | |
| `KSU_EXPECTED_HASH` | Customize the hash of the KernelSU manager signature. | |
| `KSU_REVERT` | Revert the commit that removed non-GKI support. | `true` |
| `ADD_KPROBES_CONFIG` | Used in the installation of KernelSU via kprobe. | `false` |
| `KSU_HOOKS_PATCH` | Automatically patch kernel source code to support KernelSU. | `false` |

### APatch

| Option | Description | Default Value |
| --- | --- | --- |
| `ADD_APATCH_SUPPORT` | Enable [APatch](https://apatch.dev/what-is-apatch.html) support. | `false` |
| `FIX_APATCH_OPENELA` | Provides a fix for an APatch issue. | `false` |

### Clang

| Option | Description | Default Value |
| --- | --- | --- |
| `USE_CUSTOM_CLANG` | Use a non-official clang such as [proton-clang](https://github.com/kdrag0n/proton-clang). | `true` |
| `CUSTOM_CLANG_SOURCE` | The source of the custom clang. | `https://github.com/ZyCromerZ/Clang/releases/download/21.0.0git-20250415-release/Clang-21.0.0git-20250415.tar.gz` |
| `CUSTOM_CLANG_BRANCH` | The branch of the custom clang. | |
| `CLANG_BRANCH` | The Google main branch to use. | `master-kernel-build-2022` |
| `CLANG_VERSION` | The Clang version to use. | `r450784e` |

### GCC

| Option | Description | Default Value |
| --- | --- | --- |
| `ENABLE_GCC_AOSP` | Enables usage of standart GCC toolchain. | `false` |
| `ENABLE_GCC_ARM64` | Enable GCC 64C cross-compiler. | `true` |
| `ENABLE_GCC_ARM32` | Enable GCC 32C cross-compiler. | `true` |

### Custom GCC

| Option | Description | Default Value |
| --- | --- | --- |
| `USE_CUSTOM_GCC` | Enable custom GCC toolchain. | `false` |
| `USE_CUSTOM_GCC_64` | Enable custom GCC 64-bit toolchain. | `true` |
| `CUSTOM_GCC_64_SOURCE` | Custom GCC 64-bit toolchain source. | `https://snapshots.linaro.org/gnu-toolchain/14.0-2023.06-1/aarch64-linux-gnu/gcc-linaro-14.0.0-2023.06-x86_64_aarch64-linux-gnu.tar.xz` |
| `CUSTOM_GCC_64_BRANCH` | Custom GCC 64-bit toolchain branch. | |
| `CUSTOM_GCC_64_BIN` | Custom GCC 64-bit toolchain binary name. | `aarch64-linux-gnu` |
| `USE_CUSTOM_GCC_32` | Enable custom GCC 32-bit toolchain. | `true` |
| `CUSTOM_GCC_32_SOURCE` | Custom GCC 32-bit toolchain source. | `https://snapshots.linaro.org/gnu-toolchain/14.0-2023.06-1/arm-linux-gnueabihf/gcc-linaro-14.0.0-2023.06-x86_64_arm-linux-gnueabihf.tar.xz` |
| `CUSTOM_GCC_32_BRANCH` | Custom GCC 32-bit toolchain branch. | |
| `CUSTOM_GCC_32_BIN` | Custom GCC 32-bit toolchain binary name. | `arm-linux-gnueabihf` |

### Miscellaneous

| Option | Description | Default Value |
| --- | --- | --- |
| `EXTRA_CMDS` | Additional compilation commands. | `LLVM=1 LLVM_IAS=1 LD=ld.lld AS=llvm-as AR=llvm-ar NM=llvm-nm OBJCOPY=llvm-objcopy OBJDUMP=llvm-objdump READELF=llvm-readelf STRIP=llvm-strip CROSS_COMPILE=aarch64-linux-gnu- CROSS_COMPILE_ARM32=arm-linux-gnueabi- CROSS_COMPILE_COMPAT=arm-linux-gnueabi- CONFIG_NO_ERROR_ON_MISMATCH=y TARGET_BUILD_VARIANT=user` |
| `USE_CUSTOM_ANYKERNEL3` | Use custom AnyKernel3. | `true` |
| `CUSTOM_ANYKERNEL3_SOURCE` | The source of the custom AnyKernel3. | `https://github.com/Jbub5/AnyKernel3.git` |
| `CUSTOM_ANYKERNEL3_BRANCH` | The branch of the custom AnyKernel3. | `proton` |
| `NEED_DTBO` | Upload DTBO. | `false` |
| `BUILD_BOOT_IMG` | Build boot.img. | `false` |
| `SOURCE_BOOT_IMAGE` | The source boot image. | `https://raw.githubusercontent.com/xiaoleGun/KernelSU_action/main/boot/boot.img` |
| `DISABLE_LTO` | Disable LTO. | `false` |
| `DISABLE_CC_WERROR` | Disable CC_WERROR. | `false` |
| `ENABLE_PYTHON2` | Enable python2. | `false` |
| `FIX_WIFI_SPEED` | Fix wifi speed. | `false` |
| `REMOVE_UNUSED_PACKAGES` | Remove unused packages. | `false` |
| `ENABLE_CCACHE` | Enable ccache. | `false` |
| `OLD_ANDROID_SUPPORT` | Support for MIUI 12.5 and custom ROMs based on Android 11 through 12. | `false` |
| `ADD_OVERLAYFS_CONFIG` | Automatically put the configs needed for OverlayFS into your defconfig. | `false` |
| `ADD_LOCALVERSION_TO_FILENAME` | Add kernel localversion to the zip filename. | `false` |

## Thanks

- [AnyKernel3](https://github.com/osm0sis/AnyKernel3)
- [AOSP](https://android.googlesource.com)
- [KernelSU](https://github.com/tiann/KernelSU)
- [xiaoxindada](httpss://github.com/xiaoxindada)
