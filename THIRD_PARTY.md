# Source attribution and notices

The referenced `licenses/` files are included in the downloadable miner archive.

RellikRig modifications: CUDA search scheduling and native kernels, GPU pipeline
changes, compact snapshots, TLS controller, fee schedule, stats and packaging.
The RellikRig binary distribution terms are in LICENSE.txt; the licenses below apply to upstream components.
Third-party components retain their respective terms:

* Native mining reference: https://github.com/puneet-mehta/pearl-hashrate-miner
  commit a6574254cb1599046b174236ee5bea1070534517; MIT OR Apache-2.0.
* Pearl consensus/proofs and Blake3 helpers: https://github.com/pearl-research-labs/pearl
  commit 52108b61df9f73053a866c1ceed0507c79097271; upstream root ISC notice
  retained in licenses/Pearl-ISC.txt; Plonky2 notices retained separately.
* Plonky2: MIT OR Apache-2.0, with original notices retained in licenses/.
* NVIDIA CUTLASS/CUTE headers: BSD-3-Clause, licenses/CUTLASS-BSD-3-Clause.txt.
* Rust dependencies: package metadata, copyright notices and license texts in
  licenses/rust; inventory in licenses/rust-index.json. It also includes build
  dependencies for completeness. Missing non-Linux target packages are listed
  separately and their code is not shipped in this Linux binary archive.

The NVIDIA driver and system C/GCC libraries are supplied by the recipient's
operating system; they are not bundled. This package contains no Peakminer code.

The public release additionally bundles CPython 3.12, OpenSSL, libffi, bzip2,
liblzma and libexpat. Their notices and versions are in licenses/runtime and
runtime-index.json. The compiled controller uses Nuitka 4.2.1; its runtime
exception permits distribution of compiled proprietary applications. Nuitka
license and exception texts are retained. No compiler is distributed.
The NVIDIA driver and system C/GCC libraries are not bundled.
