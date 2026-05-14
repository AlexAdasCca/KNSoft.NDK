## Local Port Notes

This repository is suitable for consumption from external package managers such
as a vcpkg local port, with one important caveat:

- `KNSoft.NDK` still relies on `KNSoft.Precomp4C` to generate import libraries
  from the XML definitions under `Source/KNSoft.NDK/WinAPI/`.

Practical implications for downstream packaging:

- Header-only consumers can install `Source/Include/**` directly.
- Binary consumers that need:
  - `KNSoft.NDK.WinAPI.lib`
  - `KNSoft.NDK.Ntdll.Hash.lib`
  - `KNSoft.NDK.Ntdll.CRT.lib`
  must also provide a build path for `KNSoft.Precomp4C`.

Default CRT policy:

- `Release` builds use `/MD`
- `Debug` builds use `/MDd`

This keeps `KNSoft.NDK` aligned with standard dynamic CRT consumers such as
`KNSoft.SlimDetours` and downstream applications.
