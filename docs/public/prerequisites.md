# 🚀 Prerequisites

[Public documentation](README.md)

Check these items before importing Windows resources into Microsoft Intune.

> [!IMPORTANT]
> Confirm the target tenant and review each resource before import. Package names and policy names do not replace checking the licensing and service requirements for individual settings.

---

## 🔐 Licensing and platform

The repository provides `BP`, `E3-E5`, and `E5` Basic packages, plus matching Adv package names. Licence builds are cumulative; confirm the required licences and service availability for every policy you intend to use.

Check the Windows version, device join/enrollment state, and management scenario required by the selected settings. Review package overviews and manifests to understand each package's scope.

## 🧰 Access and dependencies

Use an account with the Intune permissions needed to import and manage the selected resources. Follow your organization's approval process for any consent requested by an import tool.

Review policy settings, descriptions, references, and assignments. Prepare tenant-specific groups, filters, applications, and service dependencies where required. Import the OneDrive and Windows ADMX files before dependent Administrative Template policies; these files are in `Windows/Full/ADMXFiles`. The OneDrive ShortPath template requires those ADMX prerequisites and configuration for the intended OneDrive folder path.

Cross-platform and tenant-wide shared dependencies are not included in this repository. Obtain only the dependencies required by the selected Windows policies.

## 🧪 Deployment readiness

Choose one package for the Windows platform. Prepare a pilot group and a way to validate deployment results and user impact before expanding assignments. Pay particular attention to restart behavior, update deadlines, security controls, and compliance actions.

See [File structure](file-structure.md) to compare package contents and [How to import](how-to-import.md) for the import sequence.
