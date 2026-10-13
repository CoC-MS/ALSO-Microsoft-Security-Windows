# 📂 File structure

[Public documentation](README.md)

This repository contains pre-generated Windows policy packages. Workload folders are directly inside each package.

## 📦 Available packages

| Package | Resources in manifest | Scope |
| --- | ---: | --- |
| [`BP`](../../Windows/BP/Config%20overview.md) | 107 | Resources marked for BP, across Basic and Adv tiers. |
| [`E5`](../../Windows/E5/Config%20overview.md) | 147 | Resources marked for BP, E3-E5, or E5, across Basic and Adv tiers. |
| [`Full`](../../Windows/Full/Config%20overview.md) | 177 | All Windows resources, plus Windows Server and Windows-targeted Conditional Access resources. |

Counts are the files listed in each package's `build-manifest.json`; they include supporting artifacts and exclude the overview and manifest. Check the selected package's manifest for its exact file list. The manifest is package metadata, not an Intune policy to import.

The licence packages are cumulative: `E5` includes BP and E3-E5 resources as well as E5 resources. Basic and Adv are tiers within the packages, not separate package choices. The `Full` package also includes resources without tier and licence markers.

> [!WARNING]
> Choose one Windows package for a tenant: `BP`, `E5`, or `Full`. Do not combine packages or import `Full` after another package; overlapping imports can create duplicate policies.

## 🗂️ Full package workloads

The `Full` package currently contains these workload folders:

`AdministrativeTemplates`, `ADMXFiles`, `ALSO_WINDOWSSERVER_POLICIES`, `Applications`, `AssignmentFilters`, `AutoPilot`, `CompliancePolicies`, `ComplianceScripts`, `ConditionalAccess`, `DeviceConfiguration`, `DeviceHealthScripts`, `DriverUpdateProfiles`, `EnrollmentStatusPage`, `Groups`, `HardwareConfigurations`, `PowerShellScripts`, `QualityUpdatePolicies`, `SettingsCatalog`, and `UpdatePolicies`. The package root also contains `MigrationTable.json`.

Browse the workloads under [`Windows/Full`](../../Windows/Full). The package includes Windows-targeted Conditional Access policies with supporting groups and named locations, a migration table, and separate Windows Server policies. Review tenant-specific values and dependencies before import. Other cross-platform shared resources are not included.

The Windows packages are a snapshot of [`packages/Windows` in the source template](https://github.com/CoC-MS/also-security-template-internal/tree/c1fbde7485a32b13a1684658de2f1e68bb571348/packages/Windows) at [revision `c1fbde7485a32b13a1684658de2f1e68bb571348`](https://github.com/CoC-MS/also-security-template-internal/commit/c1fbde7485a32b13a1684658de2f1e68bb571348). Changes to the source template do not automatically update this repository.

See [General prerequisites](general-prerequisites.md), [Windows prerequisites](windows-prerequisites.md), and [How to import](how-to-import.md) before deployment.
