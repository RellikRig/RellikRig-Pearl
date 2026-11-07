# RellikRig

**Native Pearl (PRL) GPU miner** for Windows & Linux, with optional **NOCK merge mining** (Beta).

Clean desktop GUI • Live statistics • Idle-aware mining • System tray controls  
**0% developer fee** when mining on the official Rellik pool

[Download Latest Release](https://github.com/RellikRig/RellikRig-Pearl/releases/latest) · [Changelog](CHANGELOG.md) · [Pool Dashboard](https://pearl.rellik.dev)

---

### Follow for Updates

- **X / Twitter:** [@rellikdev](https://x.com/rellikdev)
- **TikTok:** [@rellik.dev](https://www.tiktok.com/@rellik.dev)
- **Reddit:** [u/RellikDev](https://www.reddit.com/u/RellikDev)
- **Email Support:** [rellikdev@gmail.com](mailto:rellikdev@gmail.com)

---

![Dashboard](docs/Screenshots%20v1.22/Dashboard.png)  
*Main dashboard — live hashrate, shares, GPU monitoring, and terminal*

**Getting Started (sped up):**

![Getting Started](docs/Screenshots%20v1.22/GettingStarted.gif)

---

### Quick Start

1. Download the correct package for your platform (see table below)
2. Extract the full archive
3. Open **Settings** and **replace the prefilled wallet** with your own PRL receiving address
4. (Optional) Enable NOCK merge mining and enter your NOCK wallet
5. Click **Start miner**

| Platform                    | Package                                                                 | How to run              |
|----------------------------|--------------------------------------------------------------------------|-------------------------|
| Windows (Installer)        | [Install-RellikRig-Windows-1.22.zip](https://github.com/RellikRig/RellikRig-Pearl/releases/download/v1.22/Install-RellikRig-Windows-1.22.zip) | Run the installer       |
| Windows (Portable)         | [RellikRig-Windows-1.22.zip](https://github.com/RellikRig/RellikRig-Pearl/releases/download/v1.22/RellikRig-Windows-1.22.zip) | `RellikRig.exe`         |
| Linux                      | [RellikRig-Linux-1.22.zip](https://github.com/RellikRig/RellikRig-Pearl/releases/download/v1.22/RellikRig-Linux-1.22.zip) | `./RellikRig`           |
| macOS (Apple Silicon)      | [RellikRig-Mac-1.10.zip](https://github.com/RellikRig/RellikRig-Pearl/releases/download/v1.10/RellikRig-Mac-1.10.zip) | `RellikRig.app` (v1.10) |

Always verify the [SHA-256 checksums](https://github.com/RellikRig/RellikRig-Pearl/releases/download/v1.22/RELEASE-SHA256SUMS.txt) after downloading.

**Default pool:** `stratum+ssl://pearl.rellik.dev:3333`

---

<details>
<summary><strong>More Screenshots (v1.22)</strong></summary>

**Mining Settings**  
![Mining Settings](docs/Screenshots%20v1.22/Settings1.png)  
*Wallet, primary/backup pool, and engine configuration*

**NOCK Merge Mining Settings**  
![NOCK Settings](docs/Screenshots%20v1.22/Settings2.png)  
*Enable Pearl + NOCK merge mining and set your NOCK wallet*

**NOCK Tab (Active Mining)**  
![NOCK Mining](docs/Screenshots%20v1.22/Nock.png)  
*Shared GPU work and confirmed NOCK receipts*

**GPU Info**  
![GPU Info](docs/Screenshots%20v1.22/GPU.png)

**Mining Calculator**  
![Mining Calculator](docs/Screenshots%20v1.22/MiningCalculator.png)

</details>

---

### Tested Hardware

RellikRig has been tested on the following NVIDIA GPUs:

| GPU | VRAM | Observed hashrate |
|-----|------|-------------------|
| NVIDIA GeForce RTX 5080 | ~16 GB | ~241 TH/s |
| NVIDIA H100 SXM | 80 GB | 221.98 TH/s |
| NVIDIA RTX PRO 4500 Blackwell | 32 GB | 154.96 TH/s |
| NVIDIA RTX A6000 | 48 GB | 89.13 TH/s |

Other NVIDIA cards may work but have not been fully validated. Results can vary with drivers, power limits, and cooling. Please report your experience if you try a different GPU.

### Features

- Native RellikRig mining engine (NVIDIA on Windows/Linux)
- Live dashboard with hashrate, shares, GPU monitoring, and terminal
- Primary + backup pool failover with automatic return
- Idle-aware mining (automatically pauses while you're using the PC)
- System tray controls and optional start-on-launch
- Built-in mining calculator and benchmark history
- Optional **NOCK merge mining** (Beta)
- Persistent settings and mining totals outside the install folder

---

### What is Merge Mining?

Merge mining allows you to mine **two coins at the same time** with the same GPU hashrate, without needing extra hardware or significantly higher power draw.

In RellikRig this means:

- You mine **Pearl (PRL)** as the primary coin
- At the same time, the miner can also submit work for **NOCK**
- You earn potential rewards from both chains using the same GPU effort

Simply enable the feature in Settings and add your NOCK wallet address.

**Note:** NOCK merge mining is currently in **Beta**. Pearl mining continues even if NOCK work is temporarily unavailable. You may experience occasional pauses in the auxiliary work and incomplete pool-side statistics while the feature matures.

---

### Fees

| Engine                        | RellikRig Developer Fee     |
|------------------------------|-----------------------------|
| Native engine on Rellik Pool | **0%**                      |
| Native engine on other pools | **2%**                      |

Pool fees are separate. The official Rellik Pool currently charges **1%**.

---

### NOCK Merge Mining (Beta)

1. Go to **Settings**
2. Enable merged mining (Pearl + NOCK)
3. Enter your own **NOCK** receiving address
4. Save settings and restart the miner

Pearl mining continues running even if NOCK work pauses. Local shared GPU work is shown in MAC/s or TMAC/s.

---

### Important Notes

- **Replace the prefilled wallet address** before mining for yourself. The address included by default belongs to the project.
- Cryptocurrency miners are frequently flagged by antivirus software. Only download from this official repository and always verify checksums.
- Windows and Linux builds require a recent NVIDIA driver.
- This is closed-source software.

---

### Support & Contact

- **Email:** [rellikdev@gmail.com](mailto:rellikdev@gmail.com)
- **X:** [@rellikdev](https://x.com/rellikdev)
- **TikTok:** [@rellik.dev](https://www.tiktok.com/@rellik.dev)
- **Reddit:** [u/RellikDev](https://www.reddit.com/u/RellikDev)
- Additional support details: [SUPPORT.md](SUPPORT.md)

---

### License

See [LICENSE.txt](LICENSE.txt)
