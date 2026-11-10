# Pawse downloads

Keyboard paused. Cat welcome. Free native apps by BWE Studio.

**[Get Pawse at pawse.bwe.one](https://pawse.bwe.one/#download)**

- **Mac 1.1.2:** universal Apple silicon/Intel app, Developer ID signed and Apple notarized. Download from the website.
- **[Windows 1.0.0 preview 1](https://github.com/ess007/pawse-releases/releases/tag/windows-v1.0.0-preview.1):** x64 installer plus ARM64 and x64 portable ZIPs, quick-start guide and SHA-256 checksums.

The Windows preview is **unsigned**. Testing covers Windows 11 ARM64 in a VM, including x64 emulation, core/UI logic, keyboard-hook smoke, per-user installation, manual lock/unlock/recovery and standard uninstall. Native Intel/AMD PCs, physical keyboards, login/upgrade lifecycle and additional display/accessibility configurations still need testing. See the release notes for precise scope. Respect your device security policy; checksums establish file integrity, not trusted publisher identity.

Pawse runs locally without an account or typed-text collection. It guards against accidental pet input and is not a security lock. Save work before trying the preview.

This public repository hosts binary releases and bounded release infrastructure. Application source remains in the private canonical repository; binary release assets are attached to releases rather than committed to Git.

## Runner availability probe

The existing manual-only GitHub workflow is an availability probe, not application QA. Its x64/ARM64 jobs did not run because of an account billing restriction. No passing hosted-runner result is claimed; local Windows VM evidence is documented in the release notes. The probe does not inject input, alter policies or install the app.
