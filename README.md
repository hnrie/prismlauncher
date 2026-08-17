<p align="center">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="/program_info/org.vinilauncher.Vinilauncher.logo-darkmode.svg">
  <source media="(prefers-color-scheme: light)" srcset="/program_info/org.vinilauncher.Vinilauncher.logo.svg">
  <img alt="Vinilauncher" src="/program_info/org.vinilauncher.Vinilauncher.logo.svg" width="40%">
</picture>
</p>

<p align="center">
  A custom launcher for Minecraft that lets you easily manage multiple installations, mods and modpacks at once — <b>without ever needing a Microsoft account</b>.<br />
  This is a personal <b>fork</b> of <a href="https://github.com/PrismLauncher/PrismLauncher">Prism Launcher</a> (itself a fork of the MultiMC Launcher) and is <b>not</b> endorsed by or affiliated with either project.
</p>

## Why this fork exists

This is a personal fork (branded **Vinilauncher**) that tracks upstream Prism Launcher's `develop` branch and adds a few small changes that are not (yet) in upstream. Everything else is identical to upstream Prism Launcher.

### Offline accounts without a Microsoft account

Upstream Prism Launcher requires at least one valid Microsoft account (that owns Minecraft) before it lets you add an offline account. This fork removes that requirement: you can add an offline account from a completely fresh install, with no Microsoft sign-in at any point.

Keep in mind that offline accounts are just that — offline. They cannot join servers that enforce online-mode authentication, and their names are not verified by Mojang. If you play on such servers, you will still need a real Microsoft account.

### Fresh builds for every commit and PR

Every push and pull request is built on GitHub Actions and packaged into ready-to-run artifacts, which are uploaded to [GitHub Releases](https://github.com/hnrie/prismlauncher/releases):

- Branch pushes produce releases tagged `build-<short-sha>` (e.g. `build-4a7184d`).
- Pull requests produce releases tagged `build-pr-<number>-<short-sha>`.

Each release contains builds for **Linux** (portable tarball and AppImage for x86_64 and aarch64), **macOS** (zip and dmg) and **Windows** (MSVC and MinGW-w64, as Setup installers and portable archives, including an arm64 variant).

## Downloads

All builds are available on the [Releases page](https://github.com/hnrie/prismlauncher/releases). Pick the release whose tag matches the commit or pull request you are interested in.

Please understand that these are **development builds**: they are built from the `develop` branch (or from pull requests), contain debug information, and may be buggy or unstable. They are not intended for most users. You have been warned.

For stable, well-tested releases of the launcher itself, use the official builds from the upstream [Prism Launcher website](https://prismlauncher.org/download) — they just won't have the offline-account change from this fork.

The build status for this fork can be found in the [GitHub Actions](https://github.com/hnrie/prismlauncher/actions) tab.

## Getting help

- **Issues specific to this fork** (the offline-account change, the release builds): open an issue in this repository.
- **Bugs or features in the launcher itself**: report them upstream at <https://github.com/PrismLauncher/PrismLauncher/issues>, since the fix belongs in Prism Launcher proper. There are also many community spaces run by upstream where you can ask for general help:
  - [Discord](https://prismlauncher.org/discord)
  - [Matrix](https://prismlauncher.org/matrix)
  - [Subreddit](https://prismlauncher.org/reddit)

## Building

If you want to build this fork yourself, check the [upstream build instructions](https://prismlauncher.org/wiki/development/build-instructions). The requirements are the same as upstream: a C++23 compiler and Qt 6 (>= 6.4).

If you are packaging this fork for a distribution, set `Launcher_BUILD_PLATFORM` to a slug identifying your distribution (examples: `archlinux`, `fedora`, `nixpkgs`).

## Translations

The translation effort is shared with upstream and is hosted on [Weblate](https://hosted.weblate.org/projects/prismlauncher/launcher/). Information about translating Prism Launcher is available at <https://github.com/PrismLauncher/Translations>.

## Forking/Redistributing/Custom builds policy

You are free to fork, redistribute and provide custom builds as long as you follow the terms of the [license](LICENSE) (this is a legal responsibility), and if you made code changes rather than just packaging a custom build, please do the following as a basic courtesy:

- Make it clear that your fork is not Prism Launcher and is not endorsed by or affiliated with the Prism Launcher project (<https://prismlauncher.org>).
- Go through [CMakeLists.txt](CMakeLists.txt) and change Prism Launcher's API keys to your own or set them to empty strings (`""`) to disable them (this way the program will still compile but the functionality requiring those keys will be disabled).

If you have any questions or want any clarification on the above conditions please make an issue and ask us.

Note that if you build this software without removing the provided API keys in [CMakeLists.txt](CMakeLists.txt) you are accepting the following terms and conditions:

- [Microsoft Identity Platform Terms of Use](https://docs.microsoft.com/en-us/legal/microsoft-identity-platform/terms-of-use)
- [CurseForge 3rd Party API Terms and Conditions](https://support.curseforge.com/en/support/solutions/articles/9000207405-curse-forge-3rd-party-api-terms-and-conditions)

If you do not agree with these terms and conditions, then remove the associated API keys from the [CMakeLists.txt](CMakeLists.txt) file by setting them to an empty string (`""`).

## License [![https://github.com/PrismLauncher/PrismLauncher/blob/develop/LICENSE](https://img.shields.io/github/license/PrismLauncher/PrismLauncher?label=License&logo=gnu&color=C4282D)](LICENSE)

All launcher code is available under the GPL-3.0-only license.

The logo and related assets are under the CC BY-SA 4.0 license.
