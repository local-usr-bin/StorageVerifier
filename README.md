# StorageVerifier

StorageVerifier is a portable, file-level storage verification tool for Windows.

It writes deterministic test data to a target, then reads the data back and verifies it. It is designed to help detect storage devices that cannot reliably store and return the amount of data they claim to support.

## Download

Download the latest published build from the **Releases** section of this repository.

Current release line:

**StorageVerifier CLI v1 Preview**

Supported platform:

**Windows 10 / Windows 11 x64**

The portable package includes its own runtime. You do not need to install Python or pip.

## Quick start

Extract the ZIP, open a terminal in the extracted directory, and run:

```text
stvr.exe test <target> --mode write-verify --size <bytes>
```

Example — test 64 MiB:

```text
stvr.exe test <target> --mode write-verify --size 67108864
```

To verify an existing StorageVerifier test set:

```text
stvr.exe verify <existing-test-directory>
```

Use:

```text
stvr.exe --help
```

for the complete command-line help.

## Modes

### `write-verify`

Writes deterministic test data and then reads it back for verification.

### `write-only`

Writes the planned test data without running the verification phase.

Existing test data can later be checked with:

```text
stvr.exe verify <existing-test-directory>
```

## Safety

StorageVerifier performs file-level testing and writes test data to the selected target.

Back up important data before testing storage devices. Keep the device connected and powered during the test.

For a first run, using a small `--size` value is recommended before running larger tests.

StorageVerifier does not perform raw-device sector writes and is not a substitute for backups, SMART monitoring, or hardware-health diagnostics.

## Preview scope

CLI v1 Preview focuses on file-level storage testing on Windows x64.

The current release has representative validation on Windows 10 and Windows 11 x64, including portable execution on clean-machine test environments.

This does not guarantee compatibility with every Windows build, storage controller, USB bridge, filesystem implementation, or hardware configuration.

The Preview does not include a GUI or a WinPE-specific distribution.

## Verifying the download

The SHA-256 of each published release asset is provided in its GitHub Release notes.

On Windows PowerShell, you can calculate a downloaded file's SHA-256 with:

```powershell
Get-FileHash .\StorageVerifier-CLI-v1-Preview-win-x64.zip -Algorithm SHA256
```

Compare the result with the SHA-256 published for that exact release asset.

## License

StorageVerifier is proprietary freeware.

Free personal use and internal organizational use are permitted under the terms in `LICENSE.txt`.

Exact, unmodified official release archives may be redistributed or mirrored free of charge under the conditions in `LICENSE.txt`.

Modified or repackaged distributions are not authorized unless separate permission is granted.

Third-party components included in the portable package remain subject to their respective licenses and notices.

Copyright © 2026 猫太郎.  
Contact: 233345754@qq.com

## Repository purpose

This repository is the public distribution and release page for StorageVerifier.

The proprietary implementation source code is not published in this repository.
