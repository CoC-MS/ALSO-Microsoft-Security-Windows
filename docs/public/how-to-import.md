# 📥 How to import

[Public documentation](README.md)

Complete the [General prerequisites](general-prerequisites.md) and review the [Windows prerequisites](windows-prerequisites.md) and [File structure](file-structure.md) before importing.

Use the [Micke M Intune Management Tool](https://github.com/Micke-K/IntuneManagement) to import reviewed Intune exports. Follow the tool's current setup and authentication instructions.

> [!IMPORTANT]
> **Unzip the repository into your OneDrive folder.** Use a short, top-level destination such as `OneDrive\Intune` rather than deeply nested folders. Windows File Explorer can fail to extract these exports because of their long filenames and full paths. OneDrive does not itself remove Explorer's path limits; if extraction still fails, use an archive tool that supports long paths and verify that all files were extracted before importing.

## Download and sign in

1. Download this repository using **Code > Download ZIP**, then extract it into the OneDrive location described above.

   ![GitHub Code menu showing Download ZIP](https://github.com/user-attachments/assets/b4005205-abc8-4e9b-a8b0-d6f919f99c06)

2. Download and extract the [Intune Management Tool](https://github.com/Micke-K/IntuneManagement). On Windows, launch `start.cmd` from the extracted tool folder. The command window and tool UI will open.

   ![Intune Management Tool folder with start.cmd](https://github.com/user-attachments/assets/ae7405c2-17cb-43a1-a96e-cd60181a2619)

3. Select the sign-in icon in the upper-right corner. Sign in to the intended Microsoft Intune tenant with an account that has the required permissions. Confirm the tenant before making changes.

   ![Intune Management Tool UI with the sign-in icon in the upper-right corner](https://github.com/user-attachments/assets/2e835f79-5e07-4c7d-bd7c-5bd4976fde50)

4. If the tool requires API consent, have an administrator authorized to grant tenant-wide consent review the requested permissions. Open the sign-in menu again and select **Request Consent** if needed. Follow the tool's current authentication instructions.

   ![Sign-in menu showing Request Consent](https://github.com/user-attachments/assets/675ebdc9-dc87-4633-bfa5-fbb92f7ba53d)

These screenshots are reused from the [Conditional Access import guide](https://github.com/CoC-MS/ALSO-Microsoft-Security-Conditional-Access#how-to-import). They illustrate the shared tool workflow; use the Windows package and workload selections below, not the Conditional Access selections in that guide. The UI may differ by tool version.

## Import the selected Windows package

1. Choose one package under `Windows` and review its `Config overview.md` and `build-manifest.json`.
2. Select **Bulk > Import** in the upper-left corner of the tool.

   ![Bulk menu showing the Import action](https://github.com/user-attachments/assets/9e8b32ce-93fe-4ef8-9c19-325d138add8c)

3. Point the import workflow at your selected Windows package and select only the workload types you intend to import. Do not select the repository root or combine packages. Leave **Import assignments** unchecked.
4. Import required ADMX files before dependent Administrative Template policies. Import only the required JSON resources from the package's workload folders; the manifest and overview are metadata, not policies.
5. For Device Health Scripts, keep each JSON export with its paired detection and remediation `.ps1` files. Hardware artifacts and standalone scripts require their matching deployment workflow; do not import them as policy JSON.
6. Review the tool's results and command-window output for errors, then inspect imported resources in Intune. Update tenant-specific values, groups, filters, OneDrive paths, update rings, and scope as needed.
7. Assign reviewed policies to a pilot group, validate deployment and user impact, then expand in stages.

> [!WARNING]
> Do not combine Windows packages or bulk-import assignments. Review tenant-specific values, dependencies, and any security controls with user impact before assignment.

For import problems or documentation corrections, see [Reporting issues](reporting-issues.md).
