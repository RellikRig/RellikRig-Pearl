# Third-party components

The closed-source RellikRig application uses separately licensed components.
Their notices are included under `LICENSES` in each release.

- Native engine reference: [pearl-hashrate-miner](https://github.com/puneet-mehta/pearl-hashrate-miner), MIT / Apache-2.0.
- Consensus and proof dependencies: [Pearl](https://github.com/pearl-research-labs/pearl), ISC; Plonky2, MIT / Apache-2.0.
- CUTLASS/CuTe headers: NVIDIA BSD-3-Clause.
- Qt/PySide6 6.8.3 and Shiboken6: LGPL-3.0 (applicable bundled modules), with third-party notices under their own terms. Qt is dynamically linked and replaceable in `_internal`.
- CPython: Python Software Foundation license, including its bundled dependency notices.
- psutil: BSD-3-Clause.
- X11 idle detection: libXss, MIT/X11; see `libXss-COPYING.txt`.
- Linux idle observer: Wayland ext-idle-notify protocol definitions, MIT; see `Wayland-idle-protocol-LICENSE.txt`. Uses the system libwayland-client.
- Inter fonts: SIL Open Font License 1.1.
- PyInstaller bootloader: GPL with its exception for frozen applications. Build tools are not application source.
- Rust dependencies: see the bundled crate inventory and individual notices.

Corresponding Qt 6.8.3 and Qt for Python/PySide/Shiboken 6.8.3 source can be
obtained from [Qt’s official source archives](https://download.qt.io/official_releases/qt/6.8/6.8.3/submodules/)
and [Qt for Python source](https://download.qt.io/official_releases/QtForPython/pyside6/PySide6-6.8.3-src/).
The bundled libraries are unmodified vendor wheels. You may replace the
LGPL-covered libraries with compatible builds and debug those modifications.

No NVIDIA driver or CUDA Toolkit is distributed. PeakMiner is installed by the
user from its official distribution; no PeakMiner source or binary is included.
