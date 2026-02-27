# DaveSaah OS

This is a custom Linux distribution compiled to run inside QEMU. I do not plan 
to optimize this build to work with other virtual environments. I may create a 
separate distribution for that in the future. For now, just QEMU.

## What You Get

- **Full Linux OS:** A minimal, high-performance environment.
- **Internet Access:** Pre-configured with DHCP via VirtIO networking.
- **GNU Shell Utils:** Standard tools for systems administration.
- **Lua:** A lightweight scripting language for automation and logic.
- **Persistence:** Everything you do in the /root directory is saved to the 
    virtual disk.

## Prerequisites

Install QEMU.

## Verify Integrity

To ensure your download hasn't been tampered with, run the validation script:

```bash
chmod +x validate.sh
./validate.sh
```

Look for "Verified" and "OK" messages.

## Start the OS

```bash
chmod +x startup.sh
./startup.sh
```

## Instructions

- Password: root
- Internet test: `ping google.com`
- Exit QEMU: Press `Ctrl + a`, then `x`
- To Reset OS: Delete rootfs.ext4 and restore from original archive.

## Security & Verification

This distribution is signed with my GPG key to ensure authenticity.

- Public Key: `davesaah_pubkey.asc`
- Signed Hashes: `SHA256SUMS.asc`

If you prefer to verify manually without the script:

```bash
gpg --import davesaah_pubkey.asc
gpg --verify SHA256SUMS.asc
sha256sum -c --ignore-missing SHA256SUMS.asc
```

## File Manifest (In Release Archive)

- bzImage: The compressed Linux kernel.
- rootfs.ext4: The persistent filesystem and OS data.
- startup.sh: The optimized QEMU launch script.
- validate.sh: Integrity check tool.
