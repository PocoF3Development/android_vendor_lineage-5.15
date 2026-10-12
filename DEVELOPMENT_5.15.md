# Alioth 5.15 development build support

This repository is for Android 17 / Xiaomi alioth 5.15 kernel development.
It is not production ready. Full upstream history is preserved.

The opt-in `TARGET_KERNEL_UAPI_AUTO_EXPORTS := true` profile declares the
headers produced by native Kbuild automatic UAPI export as Soong outputs.
Header installation runs inside the normal sbox output directory, so
Android retains the headers and the source tree stays read-only.
Legacy kernel and prebuilt-header profiles retain their existing behavior.

The output inventory follows source UAPI headers and the architecture's
asm-generic wrapper lists. Unsupported generated Kbuild expressions fail
analysis instead of silently producing an incomplete header tree.

After switching this profile in an existing checkout, run the first build
with `SOONG_INCREMENTAL_ANALYSIS=false` to regenerate cached build actions.
Compile and packaging checks do not establish hardware boot or firmware
compatibility. No flashing is performed by these changes.
