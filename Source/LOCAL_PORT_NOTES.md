## Local Port Notes

This repository is suitable for consumption from external package managers such
as a vcpkg local port.

Practical implications for downstream packaging:

- Header-only consumers can install `Source/Include/**` directly.
- Binary consumers that need:
  - `KNSoft.NDK.WinAPI.lib`
  - `KNSoft.NDK.Ntdll.Hash.lib`
  - `KNSoft.NDK.Ntdll.CRT.lib`
  need `KNSoft.Precomp4C` when regenerating these libraries from the XML
  definitions under `Source/KNSoft.NDK/WinAPI/`.

Current repository layout:

- The native `KNSoft.NDK` build consumes the vendored prebuilt
  `KNSoft.Precomp4C` artifacts under `Source/3rdParty/KNSoft.Precomp4C`.
- The managed `SDK` helper is not part of the default solution build. It is a
  maintenance/codegen helper rather than a required consumer artifact for the
  NDK package itself.

Default CRT policy:

- `Release` builds use `/MD`
- `Debug` builds use `/MDd`

This keeps `KNSoft.NDK` aligned with standard dynamic CRT consumers such as
`KNSoft.SlimDetours` and downstream applications.
