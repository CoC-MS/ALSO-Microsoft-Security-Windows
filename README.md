# 🛡️ ALSO Microsoft Security - Windows

> Microsoft Intune security policy exports and supporting artifacts for Windows devices, helping organizations accelerate secure deployments and apply Microsoft security best practices.

> [!IMPORTANT]
> These exports are starting points, not ready-made tenant configurations. Review licensing, settings, tenant-specific values, dependencies, and assignments; pilot policies before expanding deployment.

| Resource | Description |
| --- | --- |
| 📦 **[Windows packages](Windows/Full/Config%20overview.md)** | Compare package scope and review package manifests. |
| 🚀 **[General prerequisites](docs/public/general-prerequisites.md)** | Check licensing, permissions, and deployment preparation.|
| 🪟 **[Windows prerequisites](docs/public/windows-prerequisites.md)** | Check Windows-specific deployment requirements.|
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
| **Device configuration and security** | Settings Catalog and Administrative Template exports, Defender controls, and device configuration policies. |
| **Provisioning** | Autopilot profiles and Enrollment Status Page configurations. |
| **Compliance and targeting** | Defender for Endpoint compliance and device-risk policies, a compliance script, and Windows assignment filters in `Full`. |
| **Updates** | Windows Update rings, driver update profiles, and a Hotpatch quality-update policy in `Full`. |
| **Scripts and hardware** | Device Health Scripts, a PowerShell script, and Dell/HP BIOS-related artifacts, depending on the package. |
| **Applications and prerequisites** | Company Portal and Microsoft 365 Apps exports, plus OneDrive and Windows ADMX exports in `Full`. |

Notable capabilities include scheduled restart and disk-cleanup settings, Windows Hotpatch prerequisites and update policy, and Defender/Secure Score detection and remediation scripts in advanced `E3-E5` and `E5` packages. Review user impact, device and service prerequisites, and licensing before deployment.

---

Start with [General prerequisites](docs/public/general-prerequisites.md) and [Windows prerequisites](docs/public/windows-prerequisites.md), choose a package using [File structure](docs/public/file-structure.md), then follow [How to import](docs/public/how-to-import.md).
