# 📥 How to import

[Public documentation](README.md)

Complete the [General prerequisites](general-prerequisites.md) and review the [Windows prerequisites](windows-prerequisites.md) and [File structure](file-structure.md) before importing.

Use the [Micke M Intune Management Tool](https://github.com/Micke-K/IntuneManagement) to import reviewed Intune exports. Follow the tool's current setup and authentication instructions.

1. Download and extract this repository and the Intune Management Tool.
2. Sign in to the intended Microsoft Intune tenant with an account that has the required permissions. Confirm the tenant before making changes.
3. Choose one package under `Windows` and review its `Config overview.md` and `build-manifest.json`.
4. Import required ADMX files before dependent Administrative Template policies. Import only the required JSON resources from the package's workload folders; the manifest and overview are metadata, not policies.
5. For Device Health Scripts, keep each JSON export with its paired detection and remediation `.ps1` files. Hardware artifacts and standalone scripts require their matching deployment workflow; do not import them as policy JSON.
6. Inspect imported resources in Intune. Update tenant-specific values, groups, filters, OneDrive paths, update rings, and scope as needed.
7. Assign reviewed policies to a pilot group, validate deployment and user impact, then expand in stages.

> [!WARNING]
> Do not combine Windows packages or bulk-import assignments. Review tenant-specific values, dependencies, and any security controls with user impact before assignment.

For import problems or documentation corrections, see [Reporting issues](reporting-issues.md).
