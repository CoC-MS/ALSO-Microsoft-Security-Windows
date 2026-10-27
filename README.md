# 🛡️ ALSO Microsoft Security - Windows

> Microsoft Intune security policy exports and supporting artifacts for Windows devices, helping organizations accelerate secure deployments and apply Microsoft security best practices.

> [!IMPORTANT]
> These exports are starting points, not ready-made tenant configurations. Review licensing, settings, tenant-specific values, dependencies, and assignments; pilot policies before expanding deployment.

---

<a id="getting-started"></a>
## 🚀 Getting started

1. ✅ Review [General prerequisites](docs/public/general-prerequisites.md) and [Windows prerequisites](docs/public/windows-prerequisites.md).
2. 📂 [Download the repository ZIP](https://github.com/CoC-MS/ALSO-Microsoft-Security-Windows/archive/refs/heads/main.zip) and follow the extraction guidance in [How to import](docs/public/how-to-import.md).
3. 📥 Follow [How to import](docs/public/how-to-import.md) to import one selected package without assignments and review tenant-specific settings.
4. 🚀 Assign reviewed policies to a pilot group, check policy deployment reports and user impact, then expand in stages.

For controlled rollouts, we recommend using Microsoft's [deployment plans](https://learn.microsoft.com/en-us/intune/device-management/deployments/overview). This Intune feature is currently in public preview.

**Need help or have feedback?** See [Reporting issues](docs/public/reporting-issues.md) to report problems or suggest improvements.

> [!WARNING]
> All issues are public; do not include sensitive information.

### Quick navigation

| Section | What you will find |
| --- | --- |
| [Getting started](#getting-started) | Prerequisites, download, import, and staged rollout. |
| [Windows licensing guide](#windows-licensing-guide) | License compatibility and limitations. |
| [Windows configuration packages](#windows-configuration-packages) | Compare BP, E5, and Full and open their overviews and manifests. |
| [Windows coverage](#windows-coverage) | Areas covered by this repository. |
| [Notable capabilities](#notable-capabilities) | Key features and deployment considerations. |
| [Documentation](#documentation) | Links to supporting guides and the repository license. |

---

<a id="windows-licensing-guide"></a>
## Windows Licensing Guide

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

- Defender Antimalware
- Microsoft Defender Firewall
- Exploit Guard
- Credential Guard
- BitLocker
- BitLocker To Go

All other Defender-related configurations may require additional licensing.

> **Important:** Microsoft 365 F1 supports deployment of Intune configuration settings only. Microsoft Defender security policy settings included in this repository are not supported with F1 licensing.

#### Sensitivity-labeling availability

Sensitivity labeling has limited included functionality across licenses:

- **Microsoft 365 Business Premium:** Manual, default, and mandatory sensitivity labeling in Microsoft 365 apps only.
- **Microsoft 365 E3:** Manual, default, and mandatory sensitivity labeling in Microsoft 365 apps, plus sensitivity labeling for containers in Microsoft 365.
- **Microsoft 365 F3:** Same sensitivity-labeling capabilities as Microsoft 365 E3.
- **Microsoft 365 F1:** Manual, default, and mandatory sensitivity labeling in Microsoft 365 apps only, same as Business Premium.

**Disclaimer:** Licensing prerequisites and feature availability listed on this page may be incorrect, incomplete, or outdated. We strongly recommend verifying all licensing information against the latest official Microsoft licensing documentation before making any purchasing or deployment decisions.

**Enterprise licenses:** [Microsoft Enterprise Plan Comparison](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/education/Modern-Work-Plan-Comparison-Enterprise.pdf)

**SMB licenses:** [Microsoft SMB Plan Comparison](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/education/Modern-Work-Plan-Comparison-SMB.pdf)

---

<a id="windows-configuration-packages"></a>
## 📦 Windows configuration packages

Each package includes a `Config overview.md` and a `build-manifest.json` listing its exported resources. Manifest paths are relative to the package.
Use the linked overviews and manifests below to review each package before importing.

| Package overview | Licence scope | Scope | Resources in manifest | Manifest |
| --- | --- | --- | ---: | --- |
| [BP](Windows/BP/Config%20overview.md) | 🏷️ **BP** | BP resources, regardless of Basic or Adv tier | 107 | [BP manifest](Windows/BP/build-manifest.json) |
| [E5](Windows/E5/Config%20overview.md) | 🏷️ **BP + E5** | All licensed tiers through E5 | 147 | [E5 manifest](Windows/E5/build-manifest.json) |
| [Full](Windows/Full/Config%20overview.md) | 🏷️ **All** | All Windows resources | 177 | [Full manifest](Windows/Full/build-manifest.json) |

Manifest counts include all listed resources, including supporting artifacts; the manifest and overview are not counted. Check the selected package manifest for its exact file list.


> [!WARNING]
> Choose one Windows package per tenant: `BP`, `E5`, or `Full`. Do not combine packages or import `Full` after another package; Intune imports can create duplicate policies rather than reconcile packages. `Full` is not a guarantee that every resource is suitable for every tenant or covered by its licences.

The `BP` and `E5` packages include their scoped Windows-targeted Conditional Access policies and supporting groups. `Full` includes the complete set of these resources, named locations, and a migration table. Review these tenant-specific resources and their dependencies before import. Other cross-platform shared content is outside this repository's scope.

<a id="windows-coverage"></a>
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

<a id="notable-capabilities"></a>
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

<a id="documentation"></a>
## 📚 Documentation

| Documentation | Overview |
| --- | --- |
| 🚀 [**General prerequisites**](docs/public/general-prerequisites.md) | Check licensing, permissions, and deployment preparation. |
| 🪟 [**Windows prerequisites**](docs/public/windows-prerequisites.md) | Check Windows-specific deployment requirements. |
| 📦 [**Windows packages**](Windows/Full/Config%20overview.md) | Compare package scope and review package manifests. |
| 📖 [**Policy naming**](docs/public/policy-naming.md) | Review the naming format and existing exceptions. |
| 🏷️ [**Short-name exceptions**](docs/public/short-name-exceptions.md) | Understand why some exported resources use shorter names. |
| 📂 [**File structure**](docs/public/file-structure.md) | Find package contents and understand the manifests. |
| 📜 [**License**](LICENSE) | Read the repository license. |
