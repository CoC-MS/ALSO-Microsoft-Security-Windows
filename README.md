# 🛡️ ALSO Microsoft Security - Windows

> Microsoft Intune security policy exports and supporting artifacts for Windows devices, helping organizations accelerate secure deployments and apply Microsoft security best practices.

> [!IMPORTANT]
> These exports are starting points, not ready-made tenant configurations. Review licensing, settings, tenant-specific values, dependencies, and assignments; pilot policies before expanding deployment.

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

These are pre-generated Intune policy exports, not a Windows application or a build tool. Each package includes a `Config overview.md` and a `build-manifest.json` listing its exported resources. Manifest paths are relative to the package.

| Package | Licence scope | Edition | Exported files |
| --- | --- | --- | ---: |
| [BP-Basic](Windows/BP-Basic/Config%20overview.md) | 🏷️ **BP** | Basic | 74 |
| [BP-Adv](Windows/BP-Adv/Config%20overview.md) | 🏷️ **BP** | Adv | 12 |
| [E3-E5-Basic](Windows/E3-E5-Basic/Config%20overview.md) | 🏷️ **BP + E3-E5** | Basic | 76 |
| [E3-E5-Adv](Windows/E3-E5-Adv/Config%20overview.md) | 🏷️ **BP + E3-E5** | Adv | 46 |
| [E5-Basic](Windows/E5-Basic/Config%20overview.md) | 🏷️ **BP + E3-E5 + E5** | Basic | 76 |
| [E5-Adv](Windows/E5-Adv/Config%20overview.md) | 🏷️ **BP + E3-E5 + E5** | Adv | 50 |
| [Full](Windows/Full/Config%20overview.md) | 🏷️ **All** | Full | 154 |

Exported-file counts come from each package's manifest and include supporting scripts and artifacts, not just policies. They exclude the package overview and manifest.

Licence builds are cumulative: `E3-E5` includes `BP`, and `E5` includes both `BP` and `E3-E5`. Basic and Adv are separate editions; **Adv is not an additional layer on top of Basic**. The `Full` package also includes Windows resources without tier or licence markers. Requirements vary by resource.

> [!WARNING]
> Choose one Windows package per tenant. Do not combine Basic, Adv, and Full packages or import Full after another package; Intune imports can create duplicate policies rather than reconcile packages. Full contains all Windows resources in this repository, not a guarantee that every resource is suitable for every tenant or covered by its licences.

Cross-platform and tenant-wide supporting content is not included in this repository. Review dependencies and import only the resources required by the selected policies. Windows Server policies and other operating systems are outside this repository's scope.

## 🌐 Windows coverage

| Area | Included content |
| --- | --- |
| 🔒 **Device configuration and security** | Settings Catalog and Administrative Template exports, Defender controls, and device configuration policies. |
| 🛡️ **Attack surface reduction (ASR)** | Audit-mode and block-mode rule profiles in Basic packages and `Full`, including low-impact, Office-focused, and L2 rule sets. |
| ☁️ **Defender for Cloud Apps integration** | [Windows prerequisite guidance](docs/public/windows-prerequisites.md) for enabling the Defender for Endpoint integration in the Defender portal. This is a manual service setting, not an exported Cloud Apps policy. |
| 🚚 **Provisioning** | Autopilot profiles and Enrollment Status Page configurations. |
| ✅ **Compliance and targeting** | Defender for Endpoint compliance and device-risk policies, a compliance script, and Windows assignment filters in `Full`. |
| 🔄 **Updates** | Windows Update rings, driver update profiles, and a Hotpatch quality-update policy in `Full`. |
| 🩺 **Scripts and hardware** | Device Health Scripts, a PowerShell script, and Dell/HP BIOS-related artifacts, depending on the package. |
| 🧩 **Applications and prerequisites** | Company Portal and Microsoft 365 Apps exports, plus OneDrive and Windows ADMX exports in `Full`. |

### ✨ Notable capabilities

- 🛡️ **ASR audit and enforcement:** Profiles for assessing rule impact in audit mode and blocking risky behaviors, including Office-focused rules. Select the intended rule set and resolve overlapping settings before assignment.
- ☁️ **Cloud app discovery:** Defender for Endpoint integration with Defender for Cloud Apps supports Shadow IT discovery with user and device context. Configure the portal setting and confirm licensing and onboarding using [Windows prerequisites](docs/public/windows-prerequisites.md).
- 🔐 **Disk encryption and local administrator protection:** BitLocker OS-disk encryption and Windows LAPS settings in Basic packages and `Full`, including a separate Windows 11 24H2+ LAPS profile with automatic account management.
- 🔑 **Windows Hello for Business:** Hello configuration in Basic packages, plus passwordless and Cloud Kerberos Trust settings in Adv packages; `Full` includes both. Cloud Kerberos Trust requires separate identity-side setup.
- 🧱 **Application and credential protection:** App Control for Business (WDAC) settings for Microsoft and Intune-deployed apps in Adv packages, plus Device Guard, Credential Guard, and HVCI settings in `E3-E5-Adv` and `E5-Adv`; these are also in `Full`. Review application compatibility, hardware requirements, and reboot impact.
- 🎣 **Enhanced Phishing Protection:** Settings for malicious-site, password-reuse, and unsafe password-storage warnings in Basic packages and `Full`. Confirm supported Windows versions and sign-in scenarios.
- 🔁 **Scheduled restart and disk cleanup:** Scheduled reboot and disk-cleanup settings. Review their user impact before assignment.
- 🔥 **Windows Hotpatch:** Hotpatch prerequisite settings, plus the Hotpatch quality-update policy in `Full`. Confirm device, service, and licence prerequisites before deployment.
- 🛡️ **Defender and Secure Score remediations:** Paired detection and remediation scripts in the advanced `E3-E5` and `E5` packages.

---

## 🚀 Getting started

1. ✅ Review [General prerequisites](docs/public/general-prerequisites.md) and [Windows prerequisites](docs/public/windows-prerequisites.md).
2. 📂 Choose a package using [File structure](docs/public/file-structure.md).
3. 📥 Follow [How to import](docs/public/how-to-import.md).
