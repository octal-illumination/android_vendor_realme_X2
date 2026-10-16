# android_vendor_realme_X2

> **Note:** All documentation and code in this project are purely AI-generated.

Proprietary vendor blobs for Realme X2 (RMX1991/1992/1993) — LineageOS 24.0
(Android 17) bring-up, branch `lineage-24.0`.

**Source (authoritative):** extracted from the `RMX1992EX_11_F.26` OFP stock
firmware dump via the device tree's `extract-files.py` — plus sm6150-common
donor blobs (Adreno 618 GPU userspace attack path) where the F.26 (Android 11)
blobs are too old for A17 frameworks.

**Status:** this branch is currently a PLACEHOLDER so that `repo sync` resolves
while extraction (Phase 2b) is in progress. Vendor mk generation follows the
LineageOS convention (`vendor/realme/X2/X2-vendor.mk`).

Device tree: `octal-illumination/android_device_realme_X2` ·
Kernel: `octal-illumination/android_kernel_realme_sm6150` ·
Manifest: `octal-illumination/manifests` (branch `lineage-24.0`) ·
Workspace governance: `~/Projects/android/devices/rmx1992/roms/CRAVE-COMPLIANCE.md`
