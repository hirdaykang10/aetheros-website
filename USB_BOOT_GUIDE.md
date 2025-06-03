# USB Boot Instructions for OS Kernel

## ✅ USB Image Created Successfully!

The bootable USB image has been created as: `usb_bootable.img` (64MB)

## How to Write to Physical USB Drive

### Option 1: Using dd (Linux/macOS)
```bash
# Find your USB device (replace /dev/sdX with actual device)
lsblk
sudo dd if=usb_bootable.img of=/dev/sdX bs=4M status=progress
sudo sync
```

### Option 2: Using Balena Etcher (Windows/Linux/macOS)
1. Download Balena Etcher from https://www.balena.io/etcher/
2. Select `usb_bootable.img` as source
3. Select your USB drive as target
4. Flash the image

### Option 3: Using Rufus (Windows)
1. Download Rufus from https://rufus.ie/
2. Select your USB device
3. Select `usb_bootable.img` as disk image
4. Click START

## Boot Instructions

1. **Insert USB Drive** into target computer
2. **Boot from USB** (usually F12/F2/Delete at startup to access boot menu)
3. **Select USB Device** from boot menu
4. **GRUB Menu** will appear with options:
   - "OS Kernel (USB Boot)" - Standard boot
   - "OS Kernel (USB Boot - Serial Debug)" - With serial debugging

## What to Expect

### ✅ Successful Boot Sequence:
- GRUB bootloader loads
- Multiboot2 header detected
- 32-bit to 64-bit transition
- Serial debug output (if available):
  ```
  XABBoot: Transitioning to 64-bit mode
  CDEFGHIJ
  === OS Kernel Starting ===
  64-bit mode active, initializing subsystems...
  LStarting core OS initialization...
  MOPQRS
  ```

### ⚠️ Current Status:
- **Boot Process**: ✅ Working
- **64-bit Mode**: ✅ Working  
- **Core Initialization**: ✅ Working
- **Process Creation**: ❌ Crashes at marker 'T'

## Serial Debug Output

If the target computer has a serial port, connect it to capture debug output:
- **Baud Rate**: 9600
- **Data Bits**: 8
- **Stop Bits**: 1
- **Parity**: None

## Troubleshooting

### If USB doesn't boot:
1. Check BIOS/UEFI settings - ensure USB boot is enabled
2. Try different USB ports (USB 2.0 vs 3.0)
3. Some systems require "Legacy Boot" or "CSM" mode

### If kernel crashes:
- The kernel currently crashes during process creation
- This is a known issue being debugged
- The crash occurs after successful 64-bit mode transition

## File Details

- **Image Size**: 64MB
- **Partition Type**: FAT32 with MBR
- **Bootloader**: GRUB2 with multiboot2 support
- **Kernel**: `/boot/kernel.elf` (64-bit multiboot2)
- **Config**: `/boot/grub/grub.cfg`

## Next Steps

The USB boot mechanism is working perfectly. The remaining work is to fix the kernel crash that occurs during ProcessManager initialization. This is unrelated to the USB boot process itself.
