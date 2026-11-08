# Build and runtime status — H SON Independent Menu v3

## Completed in source

- Replaced the previous H SON menu dispatcher with an independent floating launcher and dark H SON panel.
- Preserved the four H SON feature cards and their order: Auto thay ảnh, Code gần nhất, Auto chia beat, Multi Scene.
- Added separate Objective-C modules: `HSONReplaceLayer`, `HSONLastCode`, `HSONBeatSplit`, and `HSONMultiSceneApply`.
- Added runtime class/selector guards and bounded wait/retry paths in the reconstructed feature modules.
- Removed production-source use of `VSToolOverlay`, `featureSwitchChanged:`, and the prior feature dispatcher.
- Excluded the original dylib from the independent build package; pseudocode and ARM64 disassembly remain as development references only.

## Not verified

- No Theos installation or iOS SDK is available in this container, so a native compile/package was not run.
- No iPhone/iPad running Video Star 14.3.3 is attached, so no UI, media-picker, QR import, beat-splitting, or multi-scene runtime test was performed.
- Private method signatures and object lifetimes can vary between app releases. The selector names were inferred from the supplied reverse-engineering material, not verified against a live 14.3.3 process.
- Multi Scene relies on undocumented QRCodeManager delegate/import behavior and should be considered experimental until tested.

**Status:** source reconstruction prepared; build and Video Star 14.3.3 runtime compatibility remain unverified. It is not accurate to describe this as 100% working or stable yet.

## Static checks run in this workspace

- PASS: all four menu cards map to the expected Objective-C module entry functions.
- PASS: production source contains no legacy `VSToolOverlay`, `featureSwitchChanged:`, or `HSONDispatchNativeFeature` dispatcher reference.
- PASS: delimiter-balance sanity check across all `.m` and `.h` files.
- PASS: all 20 exported bridge helpers declared in `HSONFeatureBridge.h` have implementations in `HSONFeatureBridge.m`.
- PASS: no `.dylib` is bundled in this independent source tree.

These are source-structure checks only; they do not replace an iOS SDK compile or real-device test.
