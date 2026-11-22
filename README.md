# YAASM

YAASM (Yet Another Ark Server Manager) runs and manages a fleet of ARK: Survival Ascended dedicated servers from a web UI and a command line, on Windows and Linux.

This repository only holds its releases. To install, copy one line from [yaasm.dev](https://yaasm.dev):

- Ubuntu: `curl -fsSL https://yaasm.dev/install.sh | bash`
- Windows, in PowerShell (not as Administrator): `irm https://yaasm.dev/install.ps1 | iex`

Or download the latest from [Releases](../../releases):

- `yaasm.exe` for Windows
- `yaasm-linux-amd64.tar.gz` for Linux
- `SHA256SUMS` to check either

Once installed, YAASM finds new releases here on its own and offers them on its OPS screen, or with `yaasm self-update`.

## If Windows blocks or removes yaasm.exe

`yaasm.exe` isn't code-signed yet. Windows is wary of programs it hasn't seen signed or widely used, so on some PCs:

- **Smart App Control** stops YAASM from starting, or stops its service. Windows says it blocked an app to protect you. Smart App Control can't make an exception for one program: the only way past it is to turn it off (Windows Security › App & browser control › Smart App Control). On some versions of Windows it can't be turned back on afterwards without reinstalling Windows, so decide knowing that.
- **Microsoft Defender** removes or quarantines `yaasm.exe`. Windows Security › Virus & threat protection › Protection history shows the detection. If you got the file from these releases and its checksum matches `SHA256SUMS`, it's a false positive: choose Restore (or Allow on device), and please open an issue with the detection's name so it can be reported to Microsoft.

Releases are checked against `SHA256SUMS` by the installer and by YAASM's own updates, and every release's `SHA256SUMS` is signed (`SHA256SUMS.sig`).

## Problems

Open an [issue](../../issues) with what you did, what happened, and the output of `yaasm doctor`.

## Terms

YAASM is free to use. It is provided as is, without warranty of any kind: you run it, and the game servers it manages, at your own risk, and nobody behind it is liable for what happens to your servers, saves or machines.

YAASM isn't affiliated with Studio Wildcard or Snail Games. ARK: Survival Ascended is their trademark.
