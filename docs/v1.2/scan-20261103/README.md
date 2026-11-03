# Antivirus scan report — v1.2 candidate packages

Scanned locally on **3 November 2026**, using **ClamAV 1.5.4**. These results apply only to the exact candidate hashes below, not to every RellikRig release or a future rebuild.

| Scan | Result |
|---|---|
| Standard scan, both ZIPs and extracted contents | **0 detections**, 1,817 scanned files, exit 0 |
| PUA-enabled scan, same scope | **2 flagged objects**: the Windows ZIP and its extracted GUI, both `PUA.Win.Packer.Nuitka-9992781-0`, exit 1 |
| Windows `.cmd` and `.ps1` installer scripts, PUA enabled | **0 detections**, 2 scanned files, exit 0 |

**This is not an unqualified clean report.** The standard scan found no detections, while the optional potentially unwanted application rules flagged the Windows Nuitka packaging. RellikRig is built with Nuitka; the rule name is consistent with that packaging. A PUA classification alone does not establish whether a program is malicious or safe. See [ClamAV’s PUA documentation](https://docs.clamav.net/faq/faq-pua.html).

## Exact packages

| Candidate | SHA-256 |
|---|---|
| Windows v1.2 | `001dba2cff794c0bde209e55175497bb35e2654e9c2a2fb9b344bcebb3da0ad6` |
| Linux v1.2 | `943eb3b6c17873a76281b9c82b69d794f86136466490abcf649b93ef640c0975` |

The Windows candidate matches the staged installer delivery tested by the owner. The Linux candidate includes the installed receipt-fallback GUI. Both archives passed CRC and all included per-file checksum checks before scanning; their hashes were unchanged afterwards. The installer script hashes are in the machine-readable report.

## Method and definitions

- Official ClamAV package obtained from [clamav.net](https://www.clamav.net/downloads); its detached package signature was verified with the Talos public key published there.
- FreshClam completed an authenticated definition update. Daily database **28173**, built **3 November 2026 at 06:27 UTC**; main **63**; bytecode **339**. Exact database hashes and timestamps are recorded below.
- Standard scan: **12:04:00–12:05:46 UTC**. PUA-enabled scan: **12:05:46–12:07:48 UTC**. Installer scan: **12:06:24–12:06:28 UTC**.
- ZIP archive scanning and recursive scanning of extracted files; maximum individual file 512 MiB, aggregate per scan object 2 GiB, archive recursion 30; limit-exceeded alerts enabled. No detected limit/error warning was omitted from the logs.
- Detection-only operation: no deletion, quarantine, executable modification, antivirus exclusions, or protection changes. No miner binaries were uploaded to a public scanning or sample-sharing service.
- The scanner detected the standard harmless EICAR positive-control file; that temporary test file was removed afterwards. It was not part of either package.

## Evidence

[Machine-readable report](scan-report.json) · [Standard scan log](standard.log) · [PUA scan log](with-pua.log) · [Installer scan log](installer-scan.log)

This is a **single-engine local static scan**, not an independent security audit, code-signing certificate, behavior analysis, or universal antivirus approval. The owner separately reported that Microsoft Defender did not alert during the Windows test; no independently captured Defender scan report is claimed here. A future build or definition update can produce a different result. Review detections and verify official checksums rather than disabling protection or assuming every alert is a false positive.
