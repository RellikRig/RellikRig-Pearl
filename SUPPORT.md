# Support

Need help with RellikRig? Start here.

## Contact

- **Email:** [rellikdev@gmail.com](mailto:rellikdev@gmail.com)
- **X / Twitter:** [@rellikdev](https://x.com/rellikdev)
- **Reddit:** [u/RellikDev](https://www.reddit.com/u/RellikDev)
- **TikTok:** [@rellik.dev](https://www.tiktok.com/@rellik.dev)

For technical issues, prefer GitHub Issues or email so we can track them properly.

## Before You Report a Problem

Please include:

- RellikRig version (shown in the bottom-left of the window)
- Operating system and version
- GPU model + driver version
- Pool you’re connected to
- Relevant log lines from the miner terminal (sanitized — no private keys or full wallet addresses)

Never share passwords, private keys, or seed phrases.

## Built-in Diagnostics

RellikRig includes tools to help collect information:

**Windows**
- Run `Diagnostics.bat` (creates a diagnostics ZIP)
- Run `Run-Self-Test.bat` for basic checks

**Linux**
- `./rellikrig doctor`
- `./rellikrig selftest`

Both platforms also expose a local summary at:
`http://127.0.0.1:4067/summary`  
(while the miner is running)

You can also create a diagnostics ZIP directly from the Settings page.

## Tested GPUs

The following GPUs have been tested:

| GPU | VRAM | Observed hashrate |
|-----|------|-------------------|
| NVIDIA GeForce RTX 5080 | ~16 GB | ~241 TH/s |
| NVIDIA H100 SXM (RunPod) | 80 GB | 221.98 TH/s |
| NVIDIA RTX PRO 4500 Blackwell (RunPod) | 32 GB | 154.96 TH/s |
| NVIDIA RTX A6000 (RunPod) | 48 GB | 89.13 TH/s |

Other NVIDIA cards may work but are considered unvalidated. Please report results (good or bad) if you try a different GPU.

## Common Questions

**My antivirus is flagging the miner.**  
This is common with any cryptocurrency mining software. Only download from this official repository and verify the SHA-256 checksums. Do not disable antivirus permanently.

**The prefilled wallet address isn’t mine.**  
Correct — replace it with your own PRL receiving address in Settings before mining for yourself.

**NOCK merge mining isn’t working / pausing.**  
NOCK support is still Beta. Pearl mining continues even when NOCK work is temporarily unavailable. Make sure you have entered a valid NOCK address and that the feature is enabled.

## Where to Report Issues

1. Check existing [GitHub Issues](https://github.com/RellikRig/RellikRig-Pearl/issues)
2. Open a new issue if needed, or email [rellikdev@gmail.com](mailto:rellikdev@gmail.com)
3. Attach a diagnostics ZIP when possible

See the main [README.md](README.md) for installation, features, and fee information.
