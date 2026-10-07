# 📂 File structure

[Public documentation](README.md)

This repository contains pre-generated Windows policy packages. Workload folders are directly inside each package.

## 📦 Available packages

| Package | Resources in manifest | Scope |
| --- | ---: | --- |
| [`BP-Basic`](../../Windows/BP-Basic/Config%20overview.md) | 74 | Basic resources marked for BP. |
| [`BP-Adv`](../../Windows/BP-Adv/Config%20overview.md) | 12 | Adv resources marked for BP. |
| [`E3-E5-Basic`](../../Windows/E3-E5-Basic/Config%20overview.md) | 76 | Basic resources marked for BP and E3-E5. |
| [`E3-E5-Adv`](../../Windows/E3-E5-Adv/Config%20overview.md) | 46 | Adv resources marked for BP and E3-E5. |
| [`E5-Basic`](../../Windows/E5-Basic/Config%20overview.md) | 76 | Basic resources marked for BP, E3-E5, and E5. |
| [`E5-Adv`](../../Windows/E5-Adv/Config%20overview.md) | 50 | Adv resources marked for BP, E3-E5, and E5. |
| [`Full`](../../Windows/Full/Config%20overview.md) | 154 | All Windows resources in this repository. |

Counts are the files listed in each package's `build-manifest.json`; they include supporting artifacts and exclude the overview and manifest. Check the selected package's manifest for its exact file list. The manifest is package metadata, not an Intune policy to import.

Licence builds are cumulative: `E3-E5` includes BP resources and `E5` includes BP and E3-E5 resources. Basic and Adv are separate editions. The `Full` package includes resources without tier and licence markers.

> [!WARNING]
> Choose one Windows package for a tenant. Do not combine Basic, Adv, or Full packages, or import Full after another package; overlapping imports can create duplicate policies.

## 🗂️ Full package workloads

The `Full` package currently contains these workload folders:

`AdministrativeTemplates`, `ADMXFiles`, `Applications`, `AssignmentFilters`, `AutoPilot`, `CompliancePolicies`, `ComplianceScripts`, `DeviceConfiguration`, `DeviceHealthScripts`, `DriverUpdateProfiles`, `EnrollmentStatusPage`, `HardwareConfigurations`, `PowerShellScripts`, `QualityUpdatePolicies`, `SettingsCatalog`, and `UpdatePolicies`.

Browse the workloads under [`Windows/Full`](../../Windows/Full). Review the package overview and manifest before import. Cross-platform and tenant-wide `Shared` resources described by the source template are not included in this repository.

The Windows exports are a snapshot of [`out/Windows` in the source template](https://github.com/CoC-MS/also-security-template-internal/tree/3890f64350a5be655c1ca6f8dcc760171bebb985/out/Windows) at [revision `3890f64350a5be655c1ca6f8dcc760171bebb985`](https://github.com/CoC-MS/also-security-template-internal/commit/3890f64350a5be655c1ca6f8dcc760171bebb985). Changes to the source template do not automatically update this repository.

See [Prerequisites](prerequisites.md) and [How to import](how-to-import.md) before deployment.
