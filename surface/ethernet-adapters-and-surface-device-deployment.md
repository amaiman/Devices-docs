---
title: Ethernet adapters and Surface deployment
description: Learn how to deploy Surface devices over a network, choose Ethernet adapters, and manage MAC address conflicts for efficient administration.
ms.assetid: 5273C59E-6039-4E50-96B3-426BB38A64C0
manager: frankbu
ms.localizationpriority: medium
ms.service: surface
author: coveminer
ms.author: chauncel
ms.topic: how-to
ms.date: 08/22/2024
appliesto:
- Windows 10
- Windows 11
---

# Ethernet adapters and Surface deployment

This article describes how to perform a network deployment of the latest Surface devices, including Surface Pro 3 and later.

Network deployment to Surface devices can pose some unique challenges for system administrators. Due to the lack of a native wired Ethernet adapter, administrators must provide connectivity through a removable Ethernet adapter.

## Select an Ethernet adapter for Surface devices

Before you can address how your deployment solution will recognize devices, you have to use a wired network adapter.

When selecting Ethernet adapters, the primary concern is how adapters will boot your Surface devices from the network. Suppose you're prestaging clients with Windows Deployment Services (WDS) or using Microsoft Endpoint Configuration Manager. Consider whether the removable Ethernet adapters will be dedicated to a specific Surface device or shared among multiple devices. For more information on potential conflicts with shared adapters, see [Manage MAC addresses with removable Ethernet adapters](#manage-mac-addresses) later in this article.

Booting from the network (PXE boot) is only supported when using an Ethernet adapter or docking station from Microsoft. The chipset in the Ethernet adapter or dock must be detected and configured as a boot device in the firmware of the Surface device. Microsoft Ethernet adapters, such as the Surface Ethernet Adapter and the [Surface Dock](https://www.microsoft.com/surface/accessories/surface-dock), use a chipset compatible with the Surface firmware.

The following Ethernet devices are supported for network boot with Surface devices:

- Surface Dock 2
- Surface Dock
- Surface Thunderbolt 4 Dock
- Surface USB-C to Ethernet and USB 3.0 Adapter
- Surface USB 3.0 to Gigabit Ethernet Adapter
- Microsoft USB-C Travel Hub
- Docking Station for Surface 3
- Docking Station for Surface Pro 3 
- Docking Station for Surface Pro and Surface Pro 2

Third-party Ethernet adapters are also supported for network deployment, although they don't support PXE boot. To use a third-party Ethernet adapter, you must load the drivers into the deployment boot image, and you must launch that boot image from a separate storage device, such as USB storage.

To PXE boot using Surface Thunderbolt 4 Dock with a supported Surface device, you may need to first install the latest drivers and firmware on the Surface device:  

- [Download drivers and firmware for Surface](https://support.microsoft.com/surface/download-drivers-and-firmware-for-surface-09bb2e09-2a4b-cb69-0951-078a7739e120).  

## Boot Surface devices from the network

To PXE boot from the network or boot from connected USB storage, you must instruct the Surface device to boot from an alternate boot device. You can boot from an alternate boot device during the boot-up process or alter the boot order in the system firmware to prioritize a boot device.

**To boot from an alternate boot device:**

1. Ensure the Surface device is powered off.
2. Press and hold the **Volume Down** button.
3. Press and release the **Power** button.
4. After the system begins to boot from the Ethernet adapter or USB storage, release the **Volume Down** button.

Or you can PXE boot immediately by booting into Surface UEFI and swiping left on the **PXE Network** option in the UEFI Boot configuration page.  For more information about this method, see [UEFI Boot configuration page](/surface/manage-surface-uefi-settings#uefi-boot-configuration-page). 

>[!NOTE]
>In addition to an Ethernet adapter, a keyboard must be connected to the Surface device to enter the preinstallation environment and navigate the deployment wizard.

For Windows 10, version 1511 and later, including the Windows Assessment and Deployment Kit (Windows ADK) for Windows 10 version 1511, the drivers for Microsoft Surface Ethernet Adapters are present by default. If you're using a deployment solution that uses Windows Preinstallation Environment (WinPE), like the Microsoft Deployment Toolkit, and booting from the network with PXE, ensure that your deployment solution uses the latest version of the Windows ADK.

## <a href="" id="manage-mac-addresses"></a>Manage MAC addresses with removable Ethernet adapters

Another consideration for administrators performing Windows deployment over the network is identifying computers when using the same Ethernet adapter to deploy to more than one computer. A common identifier deployment technologies use is the Media Access Control (MAC) address associated with each Ethernet adapter. However, when you use the same Ethernet adapter to deploy to multiple computers, you can only use a deployment technology that inspects MAC addresses if there's no way to differentiate the MAC address of the removable adapter when used on different computers.

The simplest solution to avoid MAC address conflicts is to provide a dedicated removable Ethernet adapter for each Surface device. This solution can make sense in many scenarios where the Ethernet adapter or the extra functionality of the docking station is used regularly. However, not all scenarios call for the extra connectivity of a docking station or support for wired networks.

Another potential solution to avoid conflict when adapters are shared is to use the [Microsoft Deployment Toolkit (MDT)](/mem/configmgr/mdt) to perform deployment to Surface devices. MDT doesn't use the MAC address to identify individual computers and thus isn't subject to this limitation. However, MDT does use Windows Deployment Services to provide PXE boot functionality and is subject to the limitations regarding prestaged clients, as described later in this section.

When you use a shared adapter for deployment, the solution for affected deployment technologies is to use another means to identify unique systems. For Configuration Manager and WDS, the key is to use the System Universal Unique Identifier (System UUID) embedded in the computer firmware by the computer manufacturer. For Surface devices, you can see this entry in the computer firmware under **Device Information**.

**To access the firmware of a Surface device:**

1. Ensure the Surface device is powered off.
2. Press and hold the **Volume Up** button.
3. Press and release the **Power** button.
4. After the machine begins to boot, release the **Volume Up** button.

When deploying with WDS, the MAC address only identifies a computer when the deployment server is configured to respond to known, prestaged clients. When prestaging a client, an administrator creates a computer account in Active Directory and defines that computer by the MAC address or the System UUID. To avoid the identity conflicts caused by shared Ethernet adapters, you should use [System UUID to define prestaged clients](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc742034(v=ws.11)). 

Alternatively, you can configure WDS to respond to unknown clients that don't require definition by either MAC address or System UUID. Select the **Respond to all client computers (known and unknown)** option on the [**PXE Response** tab](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732360(v=ws.11)) in **Windows Deployment Server Properties**.

The potential for conflicts with shared Ethernet adapters is higher with Configuration Manager. While WDS only uses MAC addresses to define individual systems, Configuration Manager uses the MAC address to determine separate systems whenever deploying to new or unknown computers. This can result in improperly configured devices or even the inability to deploy multiple systems with a shared Ethernet adapter. Several potential solutions for this situation are described in detail in [How to Use The Same External Ethernet Adapter For Multiple SCCM OSD](https://techcommunity.microsoft.com/t5/core-infrastructure-and-security/how-to-use-the-same-external-ethernet-adapter-for-multiple-sccm/ba-p/257374).
