# 0.1.4 — Windows and Linux

- Added packaged Windows support for RTX 5080.
- Windows fee: 2% (36 seconds/1800 seconds); Linux fee remains 1% (18/1800).
- Removed raw event/snapshot diagnostic JSON from the console on both platforms.
- Preserved the local stats API, GPU telemetry, full JSON logs and thermal guard.
- Native engine and CUDA kernels are unchanged from each tested platform baseline.
- 30 Windows Python/Wine tests and 26 Linux tests passed.
- Baselines: Linux 25 h 2 m, 2,302 accepted/1 stale, 239.18 TH/s; Windows
  6 h 46 m, 670 accepted/1 stale, 230.81 TH/s. No invalid proofs observed.
- Changed Windows controller still needs a native Windows soak test.
