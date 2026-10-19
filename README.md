# RellikRig · v1.0.2 Beta

A closed-source Pearl GPU miner and desktop monitor for Windows and Linux, styled to match [Rellik’s Pearl pool](https://pearl.rellik.dev/).

RellikRig includes its native NVIDIA engine, an optional PeakMiner runner, live GPU statistics, an embedded console, and system tray controls. This release is Pearl-only; it contains no Monero or NOID CPU miner.

## Download and run

Download the platform archive and `SHA256SUMS` from [GitHub Releases](https://github.com/RellikRig/RellikRig-Pearl/releases).

| Platform | Archive | Launch |
|---|---|---|
| Windows x64 | `RellikRig-Windows-1.0.2-Beta.zip` | Extract the whole folder, then open `RellikRig.exe` |
| Linux x64 | `RellikRig-Linux-1.0.2-Beta.zip` | Extract the whole folder, then run `./RellikRig` |

Keep `_internal` beside the executable. Python, Rust and the CUDA Toolkit are not required. An installed NVIDIA driver is required. The retained native profile was validated on an RTX 5080 with 16 GB VRAM; other packaged NVIDIA architectures have not received equivalent performance validation. The native RTX 5080 profile needs about 14 GB of available VRAM.

The Windows build was cross-compiled and its interface and policy tests were run under Wine. Native Windows GPU mining remains a user-test item for this beta. The Linux native engine and CUDA images are retained from the previously validated build.

## First run

1. Open **Settings → Miner**.
2. Enter your public Pearl receiving address and a worker name. The default worker is `RellikRig`; the wallet starts blank.
3. Select **RellikRig · native engine**, or select PeakMiner and extract its download into the `Peakminer` folder beside RellikRig.
4. Review the pool, save settings, then click **Start miner** on the dashboard.

The default pool is `stratum+ssl://pearl.rellik.dev:3333`. TLS certificates are verified. Custom share difficulty is optional; leave it blank for the pool’s automatic settings. Alternate pools must support compatible Pearl V3 proof submissions.

You can edit and save settings while mining. The confirmation explains that saved mining settings apply on the next miner start; stop and restart the miner to apply them now. The current session keeps its engine, wallet, pool and API settings until then.

## Engines and fees

| Selected engine | Destination | RellikRig miner fee |
|---|---|---:|
| RellikRig native | `pearl.rellik.dev:3333` over TLS | **0%** |
| RellikRig native | Any other pool | **2%** |
| PeakMiner | Any pool | **1%**, additional to PeakMiner’s own developer fee |

Pool fees are separate. The Rellik pool currently charges a 1% pool fee on block rewards; a 0% RellikRig miner fee does not remove it. PeakMiner’s own fee is controlled by PeakMiner, not this application. For example, a 2% PeakMiner fee plus the 1% RellikRig allocation leaves approximately 97.02% for user mining before pool fees and restart overhead.

Native 2% allocation uses the final 36 seconds of each 30-minute cycle. The PeakMiner runner targets 18 seconds per 30 minutes of observed active mining, retains its allocation clock across app restarts, and returns to the user wallet afterward. Allocation describes mining time, not a fixed number of shares or guaranteed revenue. Connection and kernel initialization take additional time when switching payees.

Developer work uses the selected pool and the project wallet:

`prl1pj3anxnynvpk9faqtmglf79h6g664c0t0ez3zndee4cu9k3aw82qs2gmdwc`

If the user wallet is already the project wallet, the payee is unchanged. Fee policy is automatic, with no percentage input in Settings.

## Native RellikRig engine

The app automatically selects its retained, fastest verified native profile for the detected GPU. On the validated RTX 5080, this is the smaller-A / four-chain-fold kernel. There are no experimental kernel or CPU-engine choices in this release. GPU-generated winners are independently checked on the CPU before submission; ordinary CPU use for proof validation is still necessary.

RellikRig does not change GPU clocks, voltage, fan speed or power limits. Existing tuning tools remain in control. The native temperature guard stops mining at its configured safety threshold, 83°C by default.

## PeakMiner console and monitoring

Download PeakMiner separately from its [official releases](https://github.com/peakminer/peakminer/releases). Choose **PeakMiner · console & monitor** under **Miner**, and extract the download into the empty `Peakminer` folder beside RellikRig. The app detects its executable automatically, including an extracted subfolder. Keep one version in that folder. **Settings → GPU → Open folder** opens it. **Browse…** selects a PeakMiner executable at another location. On Linux, enable the executable permission on the downloaded file before using it.

RellikRig launches and stops the selected process, displays its stdout/stderr in **Show console**, and reads its local API for the dashboard. PeakMiner is proprietary and is not bundled or redistributed in these archives. Its own license and developer fee apply.

Stop a separately running GPU miner before starting a new session. If an API port is already occupied, select a free port under **Settings → GPU** or stop the other instance. RellikRig does not terminate unrelated miners.

## Dashboard and tray

The dashboard shows hashrate, efficiency, accumulated accepted and rejected shares, GPU load, temperature, fan, power, core clock, and VRAM.

- **Mining Time:** accumulated observed mining time, retained after stopping or exiting.
- **Session Time:** active mining time since the current Start action; resets on a new session.
- **Accepted / Rejected · Total:** accumulated counters across app-controlled mining sessions and both GPU engines. These are local observations, including allocation work, not pool payout accounting.

Mining time pauses while stopped or disconnected. Totals are saved regularly and on a clean stop; an abrupt power loss can lose observations since the last save.

**Show console** also provides miner input. Type a command and press Enter or **Send command**, or use **Send key** to send text without Enter (for shortcuts such as `h`). Input goes to the running miner’s standard input, not a system shell. Supported commands and shortcuts depend on the miner; this does not add commands to engines that do not implement them.

The native console reports new jobs and accepted/rejected shares immediately, with a telemetry summary approximately once every 60 seconds. The dashboard and local API keep refreshing independently.

**Show console** opens the live output below the dashboard and expands the window within the available screen area. Metric cards and buttons retain their sizes; the dashboard scrolls on smaller screens.

Closing the window keeps mining in the tray when enabled. Right-click the tray icon for Show, Start, Stop, or **Exit RellikRig**. Exit stops the app’s mining processes. Startup at sign-in and mining on launch are optional and disabled by default.

![Pearl dashboard before mining](docs/dashboard.png)

![Dark Miner settings](docs/settings.png)

**Pool website** opens the pool in your default browser. **Your pool stats** opens its lookup page and copies the active wallet address; paste it into the lookup field. The system browser and file manager launch with their own libraries, so bundled Qt files do not override KDE’s installed version.

## Local API and saved settings

| Engine | Default local summary |
|---|---|
| RellikRig native | `http://127.0.0.1:4067/summary` |
| PeakMiner | `http://127.0.0.1:4069/summary` |

The app uses loopback APIs; it does not open firewall ports or expose them to the LAN. No analytics service is used. Your configured pool receives mining traffic, and opening a website link uses your browser.

Settings and logs are stored in the user’s application configuration directory under `RellikRig-1/settings.json`; the exact location follows Qt’s platform configuration path. Mining time and share totals are stored there too. This beta uses its own configuration and does not overwrite an earlier CPU-enabled installation’s settings or stop its CPU services.

## Troubleshooting

Beta 2 fixes a Windows startup check that incorrectly reported unused API ports as occupied. The native server now attempts the actual bind and reports the operating system error if it cannot open the API.

Use **Settings → Create diagnostics ZIP** to export the version, GPU details, recent console output and local summary. Wallet addresses are redacted in that export. Report issues with OS, driver, GPU model, selected engine, pool, and the error text at [GitHub Issues](https://github.com/RellikRig/RellikRig-Pearl/issues).

If native mining cannot find the GPU, check `nvidia-smi` and install the appropriate NVIDIA driver. If a pool rejects authorization, verify the wallet, endpoint and TLS mode. If the app says its API port is occupied, stop the competing instance or choose a different port. If the extracted folder is incomplete, extract it again without separating `_internal` from the executable.

## License and source availability

RellikRig application source is private. This repository contains documentation, screenshots and release downloads only. GitHub’s automatic “Source code” ZIP/TAR archives contain this documentation repository, not the miner implementation.

See [LICENSE.txt](LICENSE.txt) for RellikRig’s proprietary license and [THIRD_PARTY.md](THIRD_PARTY.md) plus the bundled `LICENSES` folder for open-source component notices. Those components retain their original licenses, including LGPL rights for Qt/PySide. PeakMiner is a separate product and retains its own terms.
