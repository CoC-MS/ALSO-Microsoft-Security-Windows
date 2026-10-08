# 🪟 Windows prerequisites

[Public documentation](README.md)

Check these Windows-specific Microsoft Defender settings before deploying the Windows resources. In the Defender portal, the advanced-feature switches are under **System** > **Settings** > **Endpoints** > **General** > **Advanced features** (in some layouts: **Settings** > **Endpoints** > **Advanced features**). Turn on a switch and select **Save preferences**.

| Portal | Configuration | Required value | Where to find it |
| --- | --- | --- | --- |
| Defender | Microsoft Defender for Cloud Apps | On | Defender portal > **System** > **Settings** > **Endpoints** > **General** > **Advanced features**. Find **Microsoft Defender for Cloud Apps**. |
| Defender | Share endpoint alerts with Microsoft Compliance center | On | Defender portal > **System** > **Settings** > **Endpoints** > **General** > **Advanced features**. Find **Share endpoint alerts with Microsoft Compliance center**. |
| Defender | Microsoft Intune connection | On | Defender portal > **System** > **Settings** > **Endpoints** > **General** > **Advanced features**. Find **Microsoft Intune connection**. |
| Defender | Use MDE to enforce security policies from Intune | On | Defender portal > **System** > **Settings** > **Endpoints** > **Configuration management**. Find the option to allow Defender for Endpoint to enforce endpoint security configurations. |
| Defender | Windows devices enforcement scope | All | Defender portal > **System** > **Settings** > **Endpoints** > **Configuration management** > **Enforcement scope**. Set the Windows device scope to **All**. |
| Defender | EDR in block mode | On | Defender portal > **System** > **Settings** > **Endpoints** > **General** > **Advanced features**. Find **EDR in block mode**. See Microsoft's [advanced features guide](https://learn.microsoft.com/en-us/defender-endpoint/advanced-features). |

These settings are prerequisites for the Windows security configuration. Review the selected scope carefully before applying **All**, then confirm the values in the target tenant before assigning policies. See Microsoft's [Intune and Defender for Endpoint integration guide](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/configure-integration) for the service connection and Windows integration settings.
