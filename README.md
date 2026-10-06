# 🛡️ ALSO Microsoft Security - Windows

> A collection of Microsoft Intune policy exports and supporting artifacts designed to help partners accelerate secure, managed Windows endpoint deployments.
>
> **Works with Microsoft 365 Business Premium and higher licences, depending on the policy.**

Adapted from the [ALSO Security Template](https://github.com/CoC-MS/also-security-template-internal) for the Windows packages included in this repository.

---

> [!IMPORTANT]
> **⚠️ Read this before importing policies.**
>
> Every export is a starting point. Review settings, tenant-specific values, licences, dependencies, and assignments before deployment. Import policies to a pilot group first and validate their outcome before expanding assignments.

| Resource | Description |
| --- | --- |
| 📦 **Windows packages** | See [Windows packages](#-windows-packages) to choose a licence and edition. |
| 📖 **Naming Convention** | See [Policy naming](#-policy-naming) for the standard format and exceptions. |
| 🚀 **Before Importing** | See [Before importing](#-before-importing) for import order and configuration requirements. |
| 📥 **How to Import** | See [How to import](#-how-to-import) for the Intune Management Tool workflow. |
| 🩺 **Device Health Scripts** | See [Device Health Scripts naming](Windows/Full/DeviceHealthScripts/NAMING-CONVENTION.md). |

---

## 📂 File structure

The Windows packages are organized by licence, edition, and Intune workload:

```text
Windows/
├── BP-Basic/
├── BP-Adv/
├── E3-E5-Basic/
├── E3-E5-Adv/
├── E5-Basic/
├── E5-Adv/
└── Full/
    ├── Config overview.md
    ├── build-manifest.json
    ├── AdministrativeTemplates/
    ├── ADMXFiles/
    ├── Applications/
    ├── AssignmentFilters/
    ├── AutoPilot/
    ├── CompliancePolicies/
    ├── ComplianceScripts/
    ├── DeviceConfiguration/
    ├── DeviceHealthScripts/
    ├── DriverUpdateProfiles/
    ├── EnrollmentStatusPage/
    ├── HardwareConfigurations/
    ├── PowerShellScripts/
    ├── QualityUpdatePolicies/
    ├── SettingsCatalog/
    └── UpdatePolicies/
```

Every package includes its own `Config overview.md` and `build-manifest.json`.
Workload folders are directly inside each package; only workloads with included
files are present. The tree above shows all workloads available in `Full`, not
the contents of every licence-specific package.

## 📦 Windows packages

These are ready-generated packages copied from
[`out/Windows` in the internal template](https://github.com/CoC-MS/also-security-template-internal/tree/3890f64350a5be655c1ca6f8dcc760171bebb985/out/Windows)
at source commit `3890f64350a5be655c1ca6f8dcc760171bebb985`.
The source policies and build tooling are maintained in the internal template,
not in this repository.

| Package | Licence scope | Edition | Exported files |
| --- | --- | --- | --- |
| [BP-Basic](Windows/BP-Basic) | Business Premium (`BP`) | Basic | 74 |
| [BP-Adv](Windows/BP-Adv) | Business Premium (`BP`) | Adv | 12 |
| [E3-E5-Basic](Windows/E3-E5-Basic) | `BP` and `E3-E5` | Basic | 76 |
| [E3-E5-Adv](Windows/E3-E5-Adv) | `BP` and `E3-E5` | Adv | 46 |
| [E5-Basic](Windows/E5-Basic) | `BP`, `E3-E5`, and `E5` | Basic | 76 |
| [E5-Adv](Windows/E5-Adv) | `BP`, `E3-E5`, and `E5` | Adv | 50 |
| [Full](Windows/Full) | All Windows exports; requirements vary by resource | Full | 154 |

Exported-file counts come from each package's manifest and include supporting
scripts and artifacts, not just policies. They exclude the package overview
and manifest.

Licence builds are cumulative: `E3-E5` includes `BP`, and `E5` includes both
`BP` and `E3-E5`. Basic and Adv packages contain only files explicitly marked
with the matching tier and a supported licence. **Adv is not a combined
Basic-plus-Adv package.** Windows resources without tier/licence markers are
available in `Full`.

Each manifest uses schema version `2.0`, identifies the platform as `Windows`,
and sets `rootDirectory` to `.`. Its file paths are relative to that package.
Use the package's overview and manifest to review its exact scope before import.

> [!WARNING]
> **Choose one package for a tenant. Do not combine Basic, Adv, and Full, or import Full after another package.**
>
> Intune imports can create duplicate policies rather than reconcile packages.
> `Full` means all Windows resources, not all operating systems and not a
> guarantee that every policy is covered by your tenant's licences.

Cross-platform and tenant-wide resources in the internal template's
`out/Shared/Full` are **not included here**. Review that supporting content in
the source repository and obtain only the dependencies your selected policies
require. Windows Server policies and other operating systems are also outside
this repository's scope.

## 🌐 Windows coverage

| Area | Included content |
| --- | --- |
| **Device configuration and security** | Settings Catalog and Administrative Template exports, Defender controls, and device configuration policies. |
| **Provisioning** | Autopilot profiles and Enrollment Status Page configurations. |
| **Compliance and targeting** | Compliance policies, a compliance script, and Windows assignment filters in `Full`. |
| **Updates** | Windows Update rings, driver update profiles, and a Hotpatch quality-update policy in `Full`. |
| **Scripts and hardware** | Device Health Scripts, a PowerShell script, and Dell/HP BIOS-related artifacts, depending on the package. |
| **Applications and prerequisites** | Company Portal and Microsoft 365 Apps exports, plus OneDrive and Windows ADMX exports in `Full`. |

### ✨ Notable capabilities

- **Scheduled restart and disk cleanup:** Windows configuration exports include scheduled reboot settings and a 365-day disk cleanup policy. Review their user impact before assignment.
- **Windows Hotpatch:** Settings Catalog exports include automatic remediation and VBS prerequisite settings; `Full` also contains the Hotpatch quality-update policy. Confirm device, service, and licence prerequisites before deployment.
- **Defender and Secure Score remediations:** Advanced `E3-E5` and `E5` packages include paired detection and remediation scripts alongside their JSON exports.

## 📖 Policy naming

Most policy exports use this format:

```text
<Licence> - <Company> - <Impact> - <Tier> - <Version> - <Platform> - <Category> - <Policy purpose> - <Scope>
```

### Naming components

| Component | Description | Examples |
| --- | --- | --- |
| `Licence` | Minimum licence requirement | `BP`, `E3-E5`, `E5` |
| `Company` | Template provider | `ALSO` |
| `Impact` | Expected implementation impact | `LI`, `MI`, `HI` |
| `Tier` | Baseline tier | `Basic`, `Adv` |
| `Version` | Policy version | `v1.0`, `v3.6` |
| `Platform` | Target platform | `Windows` |
| `Category` | Intune or security area | `Device Security`, `Defender` |
| `Policy purpose` | What the policy configures | `Disable AutoRun` |
| `Scope` | Assignment scope when applicable | `D`, `U` |

`D` identifies a device-targeted policy and `U` identifies a user-targeted
policy. The template convention uses ` - ` as the separator; do not use `/`
because Intune does not support it in policy names. Imported filenames and
policy names are preserved as exported, including existing separator variations.

### Short-name exceptions

Some Intune resources have restrictive name-length limits. Compliance policies,
assignment filters, and similar general resources therefore use a shorter
`ALSO`-prefixed name rather than the complete convention.

Autopilot profiles use underscore-delimited names:

```text
<Licence>_<Company>_<Impact>_<Tier>_<Version>_<Platform>_Autopilot Profile_<Purpose>
```

For Device Health Scripts, keep the JSON export and its detection and
remediation scripts together with their original matching base names.

## 🚀 Before importing

1. Choose one Windows package and read its `Config overview.md` and `build-manifest.json`.
2. Review each policy's settings and description, especially tenant-specific values, assignments, update rings, licences, and security controls.
3. Import required ADMX files before importing Administrative Template policies that depend on them. The OneDrive and Windows ADMX exports are in [`Windows/Full/ADMXFiles`](Windows/Full/ADMXFiles); obtain only the required prerequisites if using a Basic package, rather than importing all of `Full`.
4. Configure the OneDrive ShortPath Administrative Template for the customer's intended OneDrive folder path before assigning it. It requires the OneDrive and Windows ADMX files.
5. Check for required shared dependencies in the internal template; these are not bundled in this Windows-only repository.
6. Import to a pilot group, validate the result in Intune, then expand assignments in stages.

## 📥 How to import

Use the [Micke M Intune Management Tool](https://github.com/Micke-K/IntuneManagement)
to import the reviewed Intune exports.

1. Download and extract the Intune Management Tool, following its current setup requirements.
2. Start `start.cmd` and sign in to the target Microsoft Intune tenant with an account that has the required Intune permissions.
3. Import required ADMX prerequisites before dependent Administrative Template policies.
4. Browse to your selected `Windows\<package>\<workload>` folder and import the matching JSON resource. For Device Health Scripts, keep each JSON file with its paired `_DetectionScript.ps1` and `_RemediationScript.ps1` files. Package manifests and overviews are reference files, not Intune policies; hardware artifacts and standalone scripts require their matching deployment workflow.
5. Review the imported policy in Intune before assignment. Update tenant-specific values, groups, filters, OneDrive folder paths, update rings, and scope as required.
6. Assign the policy to a pilot group. Confirm the deployment result and user impact before expanding to production.

> [!WARNING]
> Do not bulk import assignments. Policies can contain security controls,
> restart behavior, update deadlines, and tenant-specific values that must be
> reviewed and approved before assignment to the target environment.

## Licence

The template and this repository are licensed under the [Apache License 2.0](LICENSE).
