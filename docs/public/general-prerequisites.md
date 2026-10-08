# 🚀 General prerequisites

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

## ⚙️ General service settings

Before deployment, confirm these general settings in the relevant portals. The portal menus can move; use the named setting on the page if your tenant shows a slightly different menu layout.

| Portal | Configuration | Required value | Where to find it |
| --- | --- | --- | --- |
| Intune | Endpoint security profile setting | Allow | Intune admin center > **Endpoint security** > **Microsoft Defender for Endpoint**. Find **Allow Microsoft Defender for Endpoint to enforce Endpoint Security Configurations** under endpoint security configuration/profile settings. |
| Intune | Connect Windows devices | On | Intune admin center > **Endpoint security** > **Microsoft Defender for Endpoint**. Under **Compliance policy evaluation**, find **Connect Windows devices to Microsoft Defender for Endpoint**. |
| Intune | Windows diagnostic data features | Enabled and confirmed | Intune admin center > **Tenant administration** > **Connectors and tokens** > **Windows data**. Turn on **Enable features that require Windows diagnostic data in processor configuration** and **I confirm that my tenant owns one of these licenses**. See Microsoft's [Windows diagnostic data and license verification guide](https://learn.microsoft.com/en-us/intune/privacy/enable-windows-diagnostic-data). |
| Intune | MDM user scope | All | Microsoft Entra admin center > **Identity** > **Mobility (MDM and MAM)** > **Microsoft Intune** > **MDM user scope**. Although listed here as an Intune prerequisite, this tenant-wide scope is configured in Entra. |
| Entra | Local administrator setting | No | Microsoft Entra admin center > **Identity** > **Devices** > **Device settings** > **Local administrator settings**. Review the settings that add the Global Administrator role or the registering user as a local administrator during device join; set the relevant setting(s) to **No**. See Microsoft's [local administrator settings guide](https://learn.microsoft.com/en-us/entra/identity/devices/assign-local-admin). |

## 🧪 Deployment readiness

Choose one package for the Windows platform. Prepare a pilot group and a way to validate deployment results and user impact before expanding assignments. Pay particular attention to restart behavior, update deadlines, security controls, and compliance actions.

See [File structure](file-structure.md) to compare package contents and [How to import](how-to-import.md) for the import sequence.

## 📚 Microsoft sources

Use Microsoft's documentation to confirm the requirements and current configuration steps for these Windows and tenant settings:

- **Defender for Endpoint connection and endpoint security enforcement:** [Configure Microsoft Defender for Endpoint with Intune](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/configure-integration) and [Integrate Microsoft Defender for Endpoint with Intune for device compliance](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/overview).
- **Windows diagnostic data features and licensing:** [Enable Windows diagnostic data in Intune](https://learn.microsoft.com/en-us/intune/privacy/enable-windows-diagnostic-data).
- **Windows automatic enrollment and MDM user scope:** [Enable automatic MDM enrollment for Windows](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/enable-automatic-mdm).
- **Microsoft Entra local administrator settings:** [Manage local administrators on Microsoft Entra joined devices](https://learn.microsoft.com/en-us/entra/identity/devices/assign-local-admin).
