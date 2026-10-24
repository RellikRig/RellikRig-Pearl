# RellikRig Mac 1.07 RC

Pearl GPU mining for Apple silicon, using Metal and Accelerate. This release includes the compact RellikRig dashboard, integrated console, accumulated/session shares and mining time, pause/resume, idle mining, and a local statistics API.

## Install

1. Download `RellikRig-Mac-1.07-RC.zip` and `SHA256SUMS` from the RellikRig GitHub release.
2. Verify the download with `shasum -a 256 -c SHA256SUMS` in its download directory.
3. Extract the complete archive and drag `RellikRig.app` into Applications. Keep the app bundle intact.
4. Open the app, enter your Pearl receiving address and worker under Settings → Miner, save, and click Start miner.

The default pool is `stratum+ssl://pearl.rellik.dev:3333`. The wallet is blank and automatic mining is off on a fresh installation. Existing local preferences are retained. Saved mining settings apply on the next miner start.

This is an Apple silicon arm64 build. It was tested on an M3 Pro MacBook Pro with 18 GB unified memory running macOS 27.0.1. Other chips and older macOS releases have not received the same validation. Python, Rust, Xcode, CUDA, and a separate CPU miner are not required. The bundle has a local ad-hoc signature; it is not Apple Developer ID signed or notarized, so macOS may require approval through Privacy & Security on first launch.

## Performance

The retained M3 Pro engine measured **3.02 TH/s** of useful work over a fixed ten-minute test, with consecutive five-minute halves of 3.014 and 3.031 TH/s. The one-minute range was 2.969–3.051 TH/s. That run recorded accepted pool work, passing checkpoint verification, and no errors. It used the same native engine included here; the RC changes the wrapper's version, defaults, and fee policy. This is a measured result on one system, not a guaranteed rate for every Mac or a fresh pool-credit comparison against another miner. Power, thermals, battery mode, other applications, and pool jobs affect performance.

The M3 Pro profile runs a disjoint combination of Metal matrix work and persistent Accelerate/BNNS CPU workers. Winning work passes independent consensus verification before submission. The Mac hashrate uses the same Pearl work units as the NVIDIA build, but the compute paths are different.

## Miner fee

| Destination | RellikRig miner fee |
|---|---:|
| `pearl.rellik.dev:3333` using TLS | **0%** |
| Other compatible Pearl pools | **2%** |

The policy matches native Linux/Windows RellikRig and is applied automatically by the controller. A saved percentage or legacy `--dev-fee` argument cannot override it. The 2% allocation is 36 seconds per 30-minute cycle, with the project wallet as payee; switching and preparation have overhead. Pool fees are separate. The Rellik pool's published pool fee still applies when its miner fee is 0%.

This Mac build uses its bundled native Metal engine. PeakMiner is not included, and PeakMiner monitoring is a Linux/Windows feature. The empty `Peakminer` directory contains no miner or downloader.

## Controls and statistics

- Start / Stop controls the app's mining session. Pause / Resume suspends mining without discarding accumulated totals.
- Settings → Miner includes idle mining, keep-awake behavior, startup, the wallet, worker, pool, and optional difficulty. Automatic startup and mining are disabled by default.
- Settings → API opens `http://127.0.0.1:4067/summary`. It is read-only and bound to loopback, with no firewall changes or LAN exposure.
- Accepted and rejected cards label Total and Session separately. Mining Time accumulates across sessions; Session Time measures the current mining session. History and estimates are local observations, not payout accounting.
- GPU/system readings come from the Mac telemetry helper. The power figure is system/SoC power and should not be directly compared with an NVIDIA GPU-only power reading.
- Close-to-menu-bar behavior is configurable. Exit stops the app-controlled mining processes. The app does not adjust hardware clocks or voltage.

Settings and logs are saved under `~/Library/Application Support/RellikRig/`. Stop mining before launching another GPU miner. If port 4067 is occupied, close the competing miner/API process before starting this one.

## Command line

The packaged controller can be used without the dashboard:

```sh
/Applications/RellikRig.app/Contents/MacOS/RellikRig --controller mine \
  --wallet YOUR_PEARL_ADDRESS --worker MacBook \
  --host pearl.rellik.dev --port 3333
```

The controller requires a compatible Pearl V3/GZIP-v2 TLS endpoint. Do not use the Mac binary on Linux, Windows, or an Intel Mac.

## Source and notices

RellikRig's application implementation remains private. This distribution contains compiled application files, public documentation, checksums, and license notices. No wallet seed, private key, user configuration, development source checkout, or PeakMiner binary is included. GitHub's automatic source archives contain the documentation repository only.

See `LICENSE.txt`, `THIRD_PARTY.md`, and `LICENSES/` for component terms. Qt/PySide libraries are dynamically linked inside `RellikRig.app/Contents/Frameworks`; their licenses preserve the right to replace and debug compatible LGPL-covered components.
