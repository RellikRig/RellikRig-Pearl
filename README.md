# RellikRig Pearl — 0.2.0 Beta




RellikRig is a graphical NVIDIA Pearl miner for Windows and Linux. Version 0.2.0 Beta is a self-contained desktop app for configuring the pool and wallet, starting or stopping mining, viewing live share and GPU information, using the system tray, and exporting diagnostics.




The release archives contain one executable, a short launch note, and the LGPL-3.0 notice for the Qt for Python runtime. There is no terminal workflow and no external kernel folder to manage.




## Download




Download the archive for your operating system from [Releases](https://github.com/RellikRig/RellikRig-Pearl/releases), extract it to a writable folder, and run the included executable.




| Platform | Download | Developer allocation |
| --- | --- | --- |
| Windows x64 | `RellikRig-Windows-0.2.0-Beta.zip` | Defaults to 2%; configurable from 1% to 100% in Settings |
| Linux x86-64 | `RellikRig-Linux-0.2.0-Beta.zip` | Defaults to 1%; configurable from 1% to 100% in Settings |




The beta was tested on an NVIDIA GeForce RTX 5080. The dashboard reports the detected GPU, driver, CUDA version, GPU load, temperature, fan, power, clocks, and VRAM. Test other NVIDIA cards carefully and include a diagnostics ZIP with any report.




## First run




1. Run `RellikRig.exe` on Windows or `RellikRig` on Linux.
2. Open **Settings** and review the wallet, worker name, pool address, custom difficulty, and developer allocation.
3. Click **Save settings**, then use **Start miner** on the Dashboard.
4. **Show console** and **Hide console** expand or collapse the complete live miner output inside the app; the Dashboard opens in its compact layout.
5. Closing the window keeps RellikRig in the system tray by default. Right-click the tray icon and select **Exit RellikRig** to stop mining and exit.




The default settings are intentionally usable without editing:




| Setting | Default |
| --- | --- |
| Wallet | `prl1pj3anxnynvpk9faqtmglf79h6g664c0t0ez3zndee4cu9k3aw82qs2gmdwc` |
| Worker | `RellikRig` |
| Pool | `prl-us.kryptex.network:8048` |
| Custom difficulty | `2097152` |
| Windows developer allocation | `2%` |
| Linux developer allocation | `1%` |




Change the wallet if you want shares credited to your own Pearl wallet. Leaving the default wallet mines to the project wallet.




## Dashboard




The dashboard reads RellikRig's local API at `127.0.0.1:4067` and NVIDIA's local driver tools. It does not send GUI telemetry to another service. The API remains available for local monitoring tools.

![Windows dashboard while mining](docs/screenshots/windows-dashboard-running.jpg)

The bottom share cards estimate 30-minute, 3-hour, and 24-hour share counts from the current uptime and accepted-share rate. They are estimates, not pool accounting.

![Windows compact dashboard](docs/screenshots/windows-dashboard-compact.jpg)

## Settings, startup, and diagnostics

Settings includes the wallet, worker name, pool address, optional custom share difficulty, Windows developer allocation, login startup, launch mining, and close behavior. RellikRig remembers its window position and keeps a single GUI instance active.

![Windows settings](docs/screenshots/windows-settings.jpg)

**Suggestions are welcomed and encouraged.** If something fails or looks wrong, use **Create diagnostics ZIP** in Settings and attach that ZIP to a GitHub Issue. It includes the application version, GPU/driver information, local API health, and a redacted mining summary so a report can be investigated without asking you to reproduce the problem.

Include the operating system, GPU, NVIDIA driver version, pool address, and a short description of what happened. Do not include passwords, private keys, or unrelated personal files. See [SUPPORT.md](SUPPORT.md) for the reporting checklist.

## Pool and fee behavior

RellikRig uses the Pearl pool protocol with GZIP v2 proof submissions. The pool target remains authoritative even when custom difficulty is requested. The developer allocation uses the configured pool and resumes normal mining at the end of its scheduled window.

- Windows: the selected percentage is scheduled across each 1,800-second cycle. The default 2% is 36 seconds; the minimum 1% is 18 seconds.
- Linux: the selected percentage is scheduled across each 1,800-second cycle. The default 1% is 18 seconds; the maximum 100% is the full cycle.

No GPU clocks, voltage, power limit, or fan setting is changed by RellikRig.

## Beta status

The native Windows 0.2.0 Beta test started a connected RTX 5080 mining session around 238 TH/s, recorded accepted shares with zero rejected shares, detected CUDA 13.4, and kept all output in the embedded console with no Command Prompt window. This is beta software: verify behavior and stability on your own system and share diagnostics for any issue.

See [CHANGELOG.md](CHANGELOG.md), [SECURITY.md](SECURITY.md), [THIRD_PARTY.md](THIRD_PARTY.md), [LICENSES/LGPL-3.0.txt](LICENSES/LGPL-3.0.txt), and [LICENSE.txt](LICENSE.txt) for release details.

