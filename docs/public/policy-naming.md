# 📖 Policy naming

[Public documentation](README.md)

The source template's common policy naming format is:

```text
<Licence> - <Company> - <Impact> - <Tier> - <Version> - <Platform> - <Category> - <Policy purpose> - <Scope>
```

## Naming components

| Component | Description | Examples |
| --- | --- | --- |
| `Licence` | Licence classification | `BP`, `E3-E5`, `E5` |
| `Company` | Template provider | `ALSO` |
| `Impact` | Expected implementation impact | `LI`, `MI`, `HI` |
| `Tier` | Baseline tier | `Basic`, `Adv` |
| `Version` | Policy version when present | `v1.0` |
| `Platform` | Target platform | `Windows` |
| `Category` | Intune or security area | `Device Security`, `Defender` |
| `Policy purpose` | What the policy configures | `Disable AutoRun` |
| `Scope` | Assignment scope when present | `D` (device), `U` (user) |

Use ` - ` as the separator for new names; do not use `/` in Intune policy names. Names and filenames in this repository are copied exports and have not been normalized. See [Short-name exceptions](short-name-exceptions.md) for current examples.

Autopilot profiles use underscore-delimited names. Device Health Script exports use matching base names for the JSON resource and its detection and remediation scripts; keep those files together.

> [!NOTE]
> Exported names and filenames are not a substitute for reviewing a resource's settings, description, licensing, and intended deployment scope.
