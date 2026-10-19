# Changelog

## 1.0.5 Beta · 2026-10-19

- Clear stale VRAM, efficiency and unavailable GPU readings on the dashboard.
- Show Reconnecting instead of a cached mining rate when the pool connection is lost.
- Recover invalid settings fields without discarding valid preferences and share totals.
- Match tray Start/Stop availability to the active miner and preserve maximized windows when restoring from the tray.

## 1.0.4 Beta · 2026-10-19

- Moved PeakMiner executable selection, folder browsing and its note into Miner settings, visible only when PeakMiner is selected.
- Added an API tab for both engine ports and local summary page links. Running-session links retain the active port until Stop → Start applies saved changes.
- Added a GPU info tab with model, driver, VRAM, load, temperature, fan, power and clock readings, including while mining is stopped.
- Reset settings scroll position when switching tabs and clear unavailable GPU readings instead of retaining stale values.

## 1.0.3 Beta · 2026-10-19

- Added dashboard and tray Pause/Resume controls, preserving active session time, accumulated shares and fee clocks.
- Added optional idle-only mining with a configurable delay, pausing on activity and resuming after idle.
- Added an optional manual-pause resume timer in minutes; Stop cancels automatic resumes.
- Added Windows, X11 and Wayland idle detection; unavailable idle detection keeps automatic mining paused.
- Wait for owned miner cleanup before resuming, without blocking the interface on termination.

## 1.0.2 Beta · 2026-10-19

- Fixed pool website, wallet stats and PeakMiner folder links on Linux by launching the system handler without bundled Qt library/plugin paths.
- Used the Windows system URL/file handler with its normal DLL search path, restoring the app's path afterward.
- Added visible link-launch errors to the console and dashboard status.
- Your pool stats opens the lookup page and copies the active wallet address for pasting there.

## 1.0.1 Beta · 2026-10-19

- Enabled settings editing and saving while mining; the active session keeps its existing engine, connection, monitoring and fee settings until the next manual start.
- Added the save confirmation explaining how to apply settings by stopping and restarting the miner.
- Connected the PeakMiner Browse button to executable selection.
- Added console input with Send command / Enter and Send key controls. Commands are passed to the selected miner; supported shortcuts depend on that miner.

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
