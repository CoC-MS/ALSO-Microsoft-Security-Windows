# 🏷️ Short-name exceptions

[Public documentation](README.md) | [Policy naming](policy-naming.md)

Not every exported Windows resource uses the complete naming convention. Compliance policies, assignment filters, applications, and other general resources can use shorter `ALSO`-prefixed or descriptive names without licence or tier markers.

Do not infer a missing licence, tier, platform, or assignment scope from a short name. Review the resource's settings, description, dependencies, and licensing before deployment. The exports have not been renamed or normalized.

## Existing spelling and separators

The checked-in filenames retain their original spellings and use both hyphen and typographic-dash separators. Autopilot profile filenames use underscores. These are existing export names, not naming guidance for new policies.

For Device Health Scripts, keep each JSON export with its matching `_DetectionScript.ps1` and `_RemediationScript.ps1` files. See [Policy naming](policy-naming.md) for the common format and [File structure](file-structure.md) for the checked-in package contents.
