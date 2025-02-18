---
title: Surface Asset Tag Tool
description: Use the Surface Asset Tag Tool to view, assign, and modify tags on Surface devices. This guide covers requirements, instructions, and examples.
ms.service: surface
ms.localizationpriority: medium
author: coveminer
ms.author: chauncel
ms.topic: how-to
ms.reviewer: carlol
ms.date: 05/21/2024
manager: frankbu
appliesto:
- Windows 10
- Windows 11
---

# Surface Asset Tag Tool

Surface Asset Tag is a command line interface (CLI) utility
that allows you to view, assign, and modify an assigned asset tag value for Surface devices.

## System requirements

- Surface Pro 3 or later and all newer Surface devices
- Unified Extensible Firmware Interface (UEFI) firmware version 3.9.150.0 or later.

## Using Surface Asset Tag

To run Surface Asset Tag:

1. Download the [Surface IT Toolkit](https://www.microsoft.com/download/details.aspx?id=46703) and install it on the PC you use to manage devices in your organization.
2. Open [Surface IT Toolkit](surface-it-toolkit.md). Select **Tool Library** > **Surface Asset Tag** > **Save a copy** and choose **ARM64** or **X64**.

    :::image type="content" source="images/surface-asset-tag-download.png" alt-text="Screenshot of Surface Asset Tag download.":::

2. Open a command console as an Administrator and run AssetTag.exe, entering the full path to the tool.

3. Restart Surface.

    > [!NOTE]
    > After setting the asset tag, a second reboot is required before it appears in WMI.

### Asset Tag tool commands

In the following examples, AssetTag.exe is saved in a directory on a local machine (C:\assets).

To get the proposed asset tag, run **AssetTag -g**:

```console
C:\assets\AssetTag.exe -g
```

To clear the proposed asset tag, run **AssetTag -s**:

```console
C:\assets\AssetTag.exe -s
```

To set the proposed asset tag, run **AssetTag -s testassettag12**:

```
C:\assets\AssetTag.exe -s testassettag12
```

>[!TIP]
>The asset tag value must contain between 1 and 36 characters. Valid characters include A-Z, a-z, 0-9, period (.) and hyphen (-).

## Managing asset tags

You can view the existing asset tag in the UEFI settings under Device
Information (**Control Panel > Recovery > Advanced Startup > Restart now**.)

The following figure shows the results of running the Asset Tag Tool on
Surface Go.

![Results of running Surface Asset Tag tool on Surface Go.](images/assettag-fig1.png)

> **Figure 1.** Results of running Surface Asset Tag tool on Surface Go

Alternately, you can use WMI to query the existing asset tag on a device:

(Get-WmiObject -query "Select * from Win32_SystemEnclosure")

### Example

```console
C:\Windows\System32> (Get-WmiObject -query "Select * from Win32_SystemEnclosure")
```
  
### Using PowerShell

You can use the following script as a way of getting the proposed value and
interpreting any errors.

```powershell
AssetTag -g \> $asset\_tag 2\> $error\_message  
$asset\_tag\_return\_code = $LASTEXITCODE  
$asset\_tag = $asset\_tag.Trim("\`r\`n")

if ($asset\_tag\_return\_code -eq 0) {  
Write-Output ("Good Tag = " + $asset\_tag)  
} else {  
Write-Output (  
"Failure: Code = " + $asset\_tag\_return\_code +  
"Tag = " + $asset\_tag +  
"Message = " + $error\_message)

}
```

### Version history

- v193.139, released October 4, 2023. Included in [Surface IT Toolkit Library](surface-it-toolkit-library.md), April 25, 2024.

## Learn more

- [Surface IT Toolkit Library](surface-it-toolkit-library.md)
