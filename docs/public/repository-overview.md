# 🛡️ About this Windows security collection

[Public documentation](README.md)

ALSO Microsoft Security - Windows is a set of recommended security and setup settings for Windows computers at work. An IT team can use these settings with Microsoft Intune, Microsoft's service for managing company devices, as a starting point for setting up and protecting those computers.

## Why use it?

Setting up device security one setting at a time can take a lot of research and effort. This collection brings together practical starting points for common needs, such as protecting files, reducing the risk of harmful software, preparing new computers, and keeping Windows up to date. It can help an IT team get started faster and review a consistent set of recommendations instead of building everything from scratch.

The collection is useful as a reference as well as a set of files to import. Organizations can review the included recommendations, decide which fit their needs, and adapt them before use.

## What is included?

The collection contains ready-made setting files and supporting materials for several parts of managing and protecting Windows computers. For example:

- **Protecting information:** settings for encrypting a device's drive, which helps keep its data private if the device is lost.
- **Protecting against threats:** settings for Microsoft Defender, Windows' built-in security features, and controls that can help reduce risky activity.
- **Preparing devices:** setup profiles that help configure new computers for employees.
- **Keeping devices current:** update settings and checks that help an IT team see whether devices meet selected requirements.
- **Additional management tools:** scripts and hardware-related settings for certain maintenance and device-management tasks.

The settings are grouped into **BP**, **E5**, and **Full** packages. The first two group resources by licence scope; Basic and Adv identify resource tiers within them. The [package guide](file-structure.md) explains the differences and helps your IT team choose one package.

## Who is it for?

This collection is intended for organizations that manage Windows computers with Microsoft Intune. IT and security staff can use it to review, select, and apply settings. People who do not manage Intune themselves can use this page to understand what the collection is for, then share it with their organization's IT team.

## Important to know

These files are not a program to run, and they do not automatically protect a computer. An IT administrator uses Intune to review and apply selected settings. Some settings depend on the organization's Microsoft licences, existing setup, and security needs; a setting that is right for one organization may not be right for another. Review and test changes on a small group of devices before wider use.

The packages focus on Windows computers. The licence packages include scoped Windows-targeted Conditional Access resources and supporting groups. `Full` also contains the complete set of these resources, named locations, a migration table, and separate Windows Server policies; review their scope and tenant-specific values before import. It is a snapshot of recommendations, so updates to the original source do not automatically appear here.

## Getting started

If you are responsible for managing devices, begin with the [general prerequisites](general-prerequisites.md) and [Windows prerequisites](windows-prerequisites.md), then use the [package guide](file-structure.md) to choose a package. Follow [How to import](how-to-import.md) to review and apply selected files.
