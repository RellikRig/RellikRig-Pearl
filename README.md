# RellikRig Pearl 0.1.2

**Pearl V3 rank-128 mining for Linux and NVIDIA RTX 5080.**
Closed-source binary distribution with a clearly disclosed **1% developer fee**.
The miner controller, fee logic, statistics API and CUDA engine are compiled.
Implementation source and private build files are not part of this release.

## Download and run

Download the `.tar.gz` release asset and `SHA256SUMS` from [GitHub Releases](https://github.com/RellikRig/RellikRig-Pearl/releases/latest).
GitHub's automatically generated “Source code” downloads contain repository
documentation only; use the named Linux miner asset.

```bash
sha256sum -c SHA256SUMS
tar -xzf RellikRig-Pearl-0.1.2-linux-x86_64-sm120.tar.gz
cd RellikRig-Pearl-0.1.2-linux-x86_64-sm120
./rellikrig doctor
./rellikrig mine --wallet YOUR_PEARL_WALLET --worker MyRig
```

Replace `YOUR_PEARL_WALLET` with your own `prl1...` address. The binary requires
an explicit mining wallet. Keep the entire extracted folder together and run
from a writable directory. Stop other GPU compute workloads before mining.
Press Ctrl+C to stop. Run `./rellikrig --help` for options.

## Supported environment

| Item | Requirement / tested configuration |
| --- | --- |
| OS | Linux x86-64, glibc 2.34 or newer |
| GPU | NVIDIA RTX 5080, SM120; other GPUs are unvalidated |
| Driver | Tested with NVIDIA 595.91.07; older versions unvalidated |
| System packages | NVIDIA driver, CA certificates, standard C/GCC runtime |
| Python / CUDA Toolkit / Rust | Not required; application runtime is bundled |
| Default pool | `prl-us.kryptex.network:8048`, verified TLS |
| Thermal limit | 83 C by default |

The miner does not change clock, voltage, power or fan settings. Extracting it
installs no startup service. This is an experimental release with testing on
one tuned RTX 5080, not a guarantee of performance on other systems.

## Developer fee: 1%

The final **18 seconds of every 1800-second cycle** are allocated to:
`prl1pj3anxnynvpk9faqtmglf79h6g664c0t0ez3zndee4cu9k3aw82qs2gmdwc`

Developer worker: `RellikRig-DevFee`. Both allocations use your selected pool.
The schedule measures wall-clock allocation; it does not guarantee exactly 1%
of shares or revenue. Setup time and share variance affect realized work.
The cycle begins at process startup. User mining resumes after the fee window.
If your wallet is the developer wallet, the existing connection is retained.
There is no fee-disable command-line option in this public binary.

## Statistics and pool configuration

Local read-only JSON stats: http://127.0.0.1:4067/summary
Reports hashrate, acceptance/rejection counts, stale drops, GPU telemetry,
active allocation and configured fee. Use `--api-port 0` to disable it.
The log is `rellikrig.jsonl` beside the executable.

```bash
./rellikrig mine --wallet YOUR_PEARL_WALLET --worker MyRig --host POOL_HOST --port TLS_PORT
```

An alternate pool must support the same Pearl V3 TLS protocol. The bundled
OpenSSL uses the operating system CA store; `SSL_CERT_FILE` can select another
CA bundle. Certificate verification remains enabled.

## Validation

See `VALIDATION.json` for checks and the pool smoke-test results for these exact
binaries. The GPU kernel is unchanged from the previously validated native build.
Its prior independent 256-hash and production CPU proof checks passed.
This 0.1.2 package averaged 239.27 TH/s in a two-minute test with
2 accepted shares, no rejects and no stale drops; this is a short measurement,
not a long-term stability guarantee or a universal best-miner claim.

To run the included GPU/CPU proof test, stop mining first:

```bash
./rellikrig selftest
```

## Troubleshooting and support

* GPU busy: stop other miners or GPU compute processes, then retry.
* Driver/library error: check `nvidia-smi` and the supported driver above.
* TLS error: check system time and the installed CA certificates.
* No local stats: inspect the terminal and log; another process may own port 4067.
* Rejected shares: report the rejection message, driver, GPU and miner version.

Open a GitHub issue with the version, GPU/driver, sanitized command and relevant
log lines. Do not include private keys, passwords, or unrelated personal data.
See `THIRD_PARTY.md` and the `licenses/` folder inside the binary archive for retained third-party terms. The RellikRig
implementation is not open source; the public repository hosts documentation
and binary releases.
