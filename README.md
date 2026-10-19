# android_vendor_realme_X2

> **Note:** All documentation and code in this project are purely AI-generated.

Proprietary vendor blobs for Realme X2 (RMX1991/1992/1993) — LineageOS 24.0
(Android 17) bring-up, branch `lineage-24.0`.

**Source (authoritative):** extracted from the `RMX1992EX_11_F.26` OFP stock
firmware dump via the device tree's `extract-files.py` (all partition MD5s
factory-verified; yatendra1999 independent cross-check 99.5%). Current content
is pure F.26. sm6150-common donor blobs (e.g., Adreno 618 GPU userspace) may be
merged later during the A16→24.0 adaptation where F.26 blobs are too old for
A17 frameworks.

**Status:** populated — 1232 blobs (767MB import at b876aaa minus the 7 excluded
camera-AI assets, see below). Makefiles generated with LineageOS extract-utils
(lineage-24.0): `X2-vendor.mk`, `Android.bp`, `Android.mk`, `BoardConfigVendor.mk`.

## Excluded assets — how to restore

1. **Absent from RMX1992EX F.26 (17 entries)** — other-variant / test-emulation
   HALs and other-chip NFC firmware: `libaptX{,HD}_encoder.so`,
   `vendor.qti.data.factory@2.2/2.3`, `data.lce@1.0`, `mwqemadapter@1.0`,
   `latency@2.1`, `libspl.so`, `init.SN100x.nfc.rc`, `libnfc-nxp-pnscr.conf`,
   `libpnscr2.so`, `libpn553/pn557_fw.so`, `libsn100u_fw.so`.
   Not present in the F.26 dump; removed from `proprietary-files.txt`.
   If ever needed, source from donor sm6150 vendor repos.

2. **LineageOS prohibited-blob policy (2 SenseTime license files)** —
   `odm/etc/camera/license_release_fdc.lic`, `odm/etc/camera/model/license.lic`.
   Commented in `proprietary-files.txt` as `# [2b-prohibited-excluded]`.
   NEVER hosted in this repo (SenseTime DMCA history). To include in a purely
   local build: uncomment the lines and re-run `extract-files.py` against your
   own F.26 dump.

3. **Empty placeholders in stock F.26 (3 files, 0 bytes)** —
   `odm/lib64/libstblur_capture_api.so`, `vendor/lib/voc.dat.zip`,
   `vendor/etc/camera/gasryuv.model`. Commented as `# [2b-empty-in-stock]`.
   Zero content — no functional loss.

4. **LOS-24-unneeded camera-AI assets (7 files, ~48MB)** — Megvii models
   (`megvii/merged_model{,_post}`), SenseTime singleblur license
   (`singleblur/license_release.license`), `libstface_fd_api.so`,
   `libcvface_api.so`, `faceTpl0/1.rgb32`. Commented as
   `# [2b-grayzone-excluded]` in the device tree; removed from this repo's tip
   but retained in git history. Restore into a working tree:

       git checkout b876aaa -- \
         proprietary/odm/etc/camera/megvii \
         proprietary/odm/etc/camera/singleblur/license_release.license \
         proprietary/odm/lib64/libstface_fd_api.so \
         proprietary/vendor/etc/camera/faceTpl0.rgb32 \
         proprietary/vendor/etc/camera/faceTpl1.rgb32 \
         proprietary/vendor/lib64/libcvface_api.so

   then uncomment the matching lines in the device tree's
   `proprietary-files.txt` and re-run:
   `python3 extract-files.py --regenerate_makefiles`.

Device tree: `octal-illumination/android_device_realme_X2` ·
Kernel: `octal-illumination/android_kernel_realme_sm6150` ·
Manifest: `octal-illumination/manifests` (branch `lineage-24.0`) ·
Workspace governance: `~/Projects/android/devices/rmx1992/roms/CRAVE-COMPLIANCE.md`
