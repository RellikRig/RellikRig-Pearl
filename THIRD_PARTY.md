# Third-party notices

Binary packages retain component-specific notices in licenses/ and THIRD_PARTY.md.
RellikRig-owned code remains proprietary; upstream licenses retain their rights.

Native mining reference: https://github.com/puneet-mehta/pearl-hashrate-miner
(MIT OR Apache-2.0). Pearl consensus/proofs:
https://github.com/pearl-research-labs/pearl (ISC; Plonky2 MIT OR Apache-2.0).
CUTLASS/CUTE: BSD-3-Clause. Rust dependencies retain their individual notices.

Both packages include compiled Nuitka controllers and CPython runtimes plus
required runtime libraries. Linux and Windows runtime inventories differ;
consult the package notices for exact contents. Windows includes MinGW runtime
notices and the GCC runtime exception. No compiler, NVIDIA driver or CUDA Toolkit
is distributed. No Peakminer code is used.
