# YAASM

YAASM (Yet Another Ark Server Manager) runs ARK: Survival Ascended dedicated servers for you, on Windows or Ubuntu: it downloads and updates the game server, creates a server per map, takes backups, restarts servers that crash, and keeps track of your players. You use it from a web page, a command line, or an AI assistant.

This repository holds YAASM's releases; the source isn't published here.

## Install

Copy one line from [yaasm.dev](https://yaasm.dev):

- **Windows 10/11**, in PowerShell (not as Administrator; it asks for admin rights once, to install the service):

  ```
  irm https://yaasm.dev/install.ps1 | iex
  ```

- **Ubuntu 24.04** (it asks for your sudo password):

  ```
  curl -fsSL https://yaasm.dev/install.sh | bash
  ```

The installer asks one question first: **express** (press Enter) keeps YAASM's files in suggested folders and opens the web app to your local network; **advanced** lets you choose. Both can be changed later in the app.

### What you need

<!-- TO FILL BEFORE MERGING: RAM per map, CPU, and anything else the owner wants listed. -->

- A 64-bit PC (x86_64) with Windows 10/11 or Ubuntu 24.04. On Ubuntu, YAASM runs the game's Windows server through Proton, which the installer sets up.
- Disk space: about 30 GB for the game server, which YAASM downloads itself, plus room for each server's saves and for backups.
- RAM: _to fill in_.

## After installing

1. **Open the address the installer prints** (port 8080 on that PC, for example `http://192.168.1.20:8080` from another device on your network).
2. **Create an account** on the first screen you see if anyone else is on your network. Until the first account exists, anyone who can open the page controls every server, and the page says so in red.
3. **Wait for the game server to download.** YAASM downloads it on its own after installing; the FLEET screen shows the progress. It's large, so this can take a while.
4. **Create your first server**: + NEW SERVER on FLEET. Pick the map, an admin password, and optionally a template such as Hard (official servers' difficulty).
   **Moving from another server manager?** IMPORT on the same page finds servers another tool set up and copies their saves and config in. The old folders aren't changed.
5. **Let players in.** Players connect to the server's game port (7777 for the first server, 7787 for the second, and so on; the server's page shows it), over UDP. On Windows, run `yaasm firewall` once per new server so Windows Firewall lets them in. To play from outside your home, forward that UDP port on your router to this PC.

`yaasm doctor` checks the install and says how to fix anything it finds.

## Updates

YAASM keeps the game server up to date on its own, warning players in chat before it restarts a server. It also finds new releases of itself here and offers them on its OPS screen (gear icon, top right), or with `yaasm self-update`.

## Uninstall

`yaasm uninstall` removes YAASM, its service and what the installer added, and asks first. Your servers, saves and backups stay unless you add `--purge`.

## Is it safe?

- **Every download is checked.** The installer and YAASM's own updates check each file against the release's `SHA256SUMS`, and YAASM only installs an update whose `SHA256SUMS` carries YAASM's signature (`SHA256SUMS.sig`).
- **Nothing is sent anywhere.** YAASM talks to Steam (for the game server), GitHub (for its own updates), and your game servers. It has no account system of its own online, no telemetry, and opens nothing to the internet.
- **`yaasm.exe` isn't code-signed by a certificate yet**, so Windows may be wary of it; see below.

## If Windows blocks or removes yaasm.exe

Windows is cautious about programs it hasn't seen signed or widely used. On some PCs:

- **Microsoft Defender removes or quarantines `yaasm.exe`.** Check that the file is genuine first: in PowerShell, `Get-FileHash yaasm.exe` should give the same hash as the `yaasm.exe` line in this release's `SHA256SUMS` (Windows prints it in capitals). If it does, Defender is mistaken: in Windows Security › Virus & threat protection › Protection history, choose the detection and Restore (or Allow on device). Please open an issue with the detection's name, so it can be reported to Microsoft.
- **Smart App Control stops YAASM from starting**, or stops its service. Smart App Control can't make an exception for one program; the only way past it is to turn it off (Windows Security › App & browser control › Smart App Control). Be aware that on some versions of Windows it can't be turned back on afterwards without resetting Windows.

## Problems

Open an [issue](../../issues) with what you did, what happened, and the output of `yaasm doctor`.

## Downloads

Each [release](../../releases) has:

- `yaasm.exe` for Windows, and `install.ps1`, the Windows installer
- `yaasm-linux-amd64.tar.gz` for Ubuntu, and `install.sh`, the Ubuntu installer
- `SHA256SUMS` and its signature, `SHA256SUMS.sig`

The install lines above always fetch the newest release. Releases marked *Pre-release* are test builds: YAASM only offers them to an install that's already running one.

## Terms

YAASM is free to use. It is provided as is, without warranty of any kind: you run it, and the game servers it manages, at your own risk, and nobody behind it is liable for what happens to your servers, saves or machines.

YAASM isn't affiliated with Studio Wildcard or Snail Games. ARK: Survival Ascended is their trademark.
