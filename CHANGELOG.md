# Changelog

## 1.0 Beta 2 · 2026-10-18

- Fixed a Windows startup check that falsely reported unused API ports as occupied.
- Let the native API server report actual bind failures with the operating system error.
- Added regression coverage for Windows socket timeouts, GUI start, real API binding and conflicts.
- Kept the default Rellik TLS pool, fee policy, native CUDA kernels, layout and optional empty Peakminer folder unchanged.

## 1.0 Beta · 2026-10-18

- Redesigned the Pearl dashboard and dark settings to match pearl.rellik.dev.
- Removed CPU mining engines, controls and payloads from this release.
- Retained the fastest verified native RTX 5080 profile with automatic GPU selection.
- Set native miner allocation to 0% on the Rellik TLS endpoint and 2% elsewhere.
- Added a PeakMiner console/monitor runner with a 1% RellikRig allocation, separate from PeakMiner's own fee.
- Retained accumulated mining time and shares, current-session time, tray controls, startup preferences and diagnostics.
- Added screen-bounded console expansion with fixed-size metric cards.
- Published closed-source Windows and Linux binary packages with third-party notices.
