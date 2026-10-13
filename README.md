# 🛡️ ALSO Microsoft Security - Windows

> Microsoft Intune security policy exports and supporting artifacts for Windows devices, helping organizations accelerate secure deployments and apply Microsoft security best practices.

> [!IMPORTANT]
> These exports are starting points, not ready-made tenant configurations. Review licensing, settings, tenant-specific values, dependencies, and assignments; pilot policies before expanding deployment.

---


## Windows 11 Licensing Guide

### ✅ E5 Folder (Full Experience)

The **E5 folder** is intended for organizations that have following licenses.

| License | Supported |
|----------|----------|
| Microsoft 365 E7 | ✅ Full support |
| Microsoft 365 E5 | ✅ Full support |
| Microsoft 365 E3 + Defender Suite | ✅ Full support (except Intune Suite features) |
| Business Premium + Defender Suite | ✅ Full support |
| Microsoft 365 F3 + Defender Suite FLW | ✅ Full support (except Intune Suite features) |
| Microsoft 365 F1 + Defender Suite FLW | ✅ Full support (except Intune Suite features) |

> **Note:** Some policies may require **Intune Suite** capabilities. Organizations without Intune Suite licensing should exclude those specific policies where indicated.

---

### ✅ BP Folder (Limited Experience)

The **Business Premium folder** is designed for organizations using Microsoft 365 Business Premium and other licenses with partial feature compatibility.

| License | Supported Features |
|----------|----------|
| Microsoft 365 Business Premium | ✅ Full support |
| Microsoft 365 E3 | ✅ Full support |
| Microsoft 365 F3 | ⚠️ Supported with limitations |
| Microsoft 365 F1 | ⚠️ Intune settings only. Defender settings are not supported. |

#### Microsoft 365 F3 Limitations

For Microsoft 365 F3, only the following Microsoft Defender security settings are supported:

- Defender Antivirus
- Microsoft Defender Firewall
- Exploit Guard
- Credential Guard
- BitLocker
- BitLocker To Go

All other Defender-related configurations may require additional licensing.

> **Important:** Microsoft 365 F1 supports deployment of Intune configuration settings only. Microsoft Defender security policy settings included in this repository are not supported with F1 licensing.

| Resource | Description |
| --- | --- |
| 📦 **[Windows packages](Windows/Full/Config%20overview.md)** | Compare package scope and review package manifests. |
| 🚀 **[General prerequisites](docs/public/general-prerequisites.md)** | Check licensing, permissions, and deployment preparation. |
| 🪟 **[Windows prerequisites](docs/public/windows-prerequisites.md)** | Check Windows-specific deployment requirements. |
| 📖 **[Policy naming](docs/public/policy-naming.md)** | Review the naming format and existing exceptions. |
| 🏷️ **[Short-name exceptions](docs/public/short-name-exceptions.md)** | Understand why some exported resources use shorter names. |
| 📂 **[File structure](docs/public/file-structure.md)** | Find package contents and understand the manifests. |
| 📥 **[How to import](docs/public/how-to-import.md)** | Review and import selected Windows exports. |
| 🐛 **[Reporting issues](docs/public/reporting-issues.md)** | Report problems without disclosing tenant information. |
| 📜 **[License](LICENSE)** | Read the repository license. |

---

## 📦 Windows configuration packages

Each package includes a `Config overview.md` and a `build-manifest.json` listing its exported resources. Manifest paths are relative to the package.
You can use these files to get a overview quickly.

| Package | Licence scope | Scope | Resources in manifest |
| --- | --- | --- | ---: |
| [BP](Windows/BP/Config%20overview.md) | 🏷️ **BP** | BP resources, regardless of Basic or Adv tier | 107 |
| [E5](Windows/E5/Config%20overview.md) | 🏷️ **BP + E5** | All licensed tiers through E5 | 147 |
| [Full](Windows/Full/Config%20overview.md) | 🏷️ **All** | All Windows resources | 177 |

Manifest counts include all listed resources, including supporting artifacts; the manifest and overview are not counted. Check the selected package manifest for its exact file list.


> [!WARNING]
> Choose one Windows package per tenant: `BP`, `E5`, or `Full`. Do not combine packages or import `Full` after another package; Intune imports can create duplicate policies rather than reconcile packages. `Full` is not a guarantee that every resource is suitable for every tenant or covered by its licences.

The `BP` and `E5` packages include their scoped Windows-targeted Conditional Access policies and supporting groups. `Full` includes the complete set of these resources, named locations, and a migration table. Review these tenant-specific resources and their dependencies before import. Other cross-platform shared content is outside this repository's scope.

## 🌐 Windows coverage

| Area | Included content |
| --- | --- |
| 🔒 **Device configuration and security** | Settings Catalog and Administrative Template exports, Defender controls, and device configuration policies. |
| 🛡️ **Attack surface reduction (ASR)** | Audit-mode and block-mode rule profiles in the `BP`, `E5`, and `Full` packages, including low-impact, Office-focused, and L2 rule sets. |
| ☁️ **Defender for Cloud Apps integration** | [Windows prerequisite guidance](docs/public/windows-prerequisites.md) for enabling the Defender for Endpoint integration in the Defender portal. This is a manual service setting, not an exported Cloud Apps policy. |
| 🚚 **Provisioning** | Autopilot profiles and Enrollment Status Page configurations. |
| ✅ **Compliance and targeting** | Defender for Endpoint compliance and device-risk policies, a compliance script, and Windows assignment filters in `Full`. |
| 🔄 **Updates** | Windows Update rings, driver update profiles, and a Hotpatch quality-update policy in `Full`. |
| 🩺 **Scripts and hardware** | Device Health Scripts, a PowerShell script, and Dell/HP BIOS-related artifacts, depending on the package. |
| 🧩 **Applications and prerequisites** | Company Portal and Microsoft 365 Apps exports, plus OneDrive and Windows ADMX exports in `Full`. |

### ✨ Notable capabilities

- 🛡️ **ASR audit and enforcement:** Profiles for assessing rule impact in audit mode and blocking risky behaviors, including Office-focused rules. Select the intended rule set and resolve overlapping settings before assignment.
- ☁️ **Cloud app discovery:** Defender for Endpoint integration with Defender for Cloud Apps supports Shadow IT discovery with user and device context. Configure the portal setting and confirm licensing and onboarding using [Windows prerequisites](docs/public/windows-prerequisites.md).
- 🔐 **Disk encryption and local administrator protection:** BitLocker OS-disk encryption and Windows LAPS settings in the `BP`, `E5`, and `Full` packages, including a separate Windows 11 24H2+ LAPS profile with automatic account management.
- 🔑 **Windows Hello for Business:** Hello, passwordless, and Cloud Kerberos Trust settings in the `BP`, `E5`, and `Full` packages. Cloud Kerberos Trust requires separate identity-side setup.
- 🧱 **Application and credential protection:** App Control for Business (WDAC) settings for Microsoft and Intune-deployed apps in `BP`, `E5`, and `Full`, plus Device Guard, Credential Guard, and HVCI settings in `E5` and `Full`. Review application compatibility, hardware requirements, and reboot impact.
- 🎣 **Enhanced Phishing Protection:** Settings for malicious-site, password-reuse, and unsafe password-storage warnings in the `BP`, `E5`, and `Full` packages. Confirm supported Windows versions and sign-in scenarios.
- 🔁 **Scheduled restart and disk cleanup:** Scheduled reboot and disk-cleanup settings. Review their user impact before assignment.
- 🔥 **Windows Hotpatch:** Hotpatch prerequisite settings, plus the Hotpatch quality-update policy in `Full`. Confirm device, service, and licence prerequisites before deployment.
- 🛡️ **Defender and Secure Score remediations:** Paired detection and remediation scripts in the `E5` and `Full` packages.

---

## 🚀 Getting started

1. ✅ Review [General prerequisites](docs/public/general-prerequisites.md) and [Windows prerequisites](docs/public/windows-prerequisites.md).
2. 📂 Choose a package using [File structure](docs/public/file-structure.md).
3. 📥 Follow [How to import](docs/public/how-to-import.md).
