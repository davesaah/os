# DaveSaah OS - Source Configuration

This directory contains the "blueprints" for the DaveSaah OS distribution. To 
keep the distribution lightweight, I've provided the configuration files rather 
than the gigabytes of raw source code.

## How to Reproduce the Build

If you wish to verify the build process, follow the follow steps: 

### Compiling Buildroot

Clone the buildroot from source:

```bash
git clone git://git.buildroot.net/buildroot --depth 1
```

Copy the configuration file to the root of the cloned repo:

```bash
cp buildroot.config ~/local_buildroot_repo/.config
```

Compile buildroot using: `make`

> You might want to update the build options from `make menuconfig` screen since
> I set the build to happen in parallel across all my 16 CPU cores.

The `rootfs.ext4` can be found at `BUILDROOT_REPO/output/images`

### Compiling The Linux Kernel

Clone the kernel from Linus’ source tree:

```bash
git clone http://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git --depth 1
cd linux
```

Copy the configuration file to the root of the cloned repo:

```bash
cp kernel.config ~/local_kernel_repo/.config
```

Compile the kernel using: `make -j$(nproc)`

The `bzImage` can be found at `KERNEL_REPO/arch/x86/boot`
