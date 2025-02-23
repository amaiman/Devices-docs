---
title: Surface Support Portal overview  
description: Discover how the Surface Support Portal offers Microsoft 365 Business customers a centralized solution for managing Surface devices, including warranty tracking, device repair requests, and Windows Autopilot registration.  
ms.service: surface  
ms.localizationpriority: medium  
author: coveminer  
ms.author: chauncel  
ms.topic: how-to  
ms.date: 09/18/2024 
ms.reviewer: cchauvet  
manager: frankbu  
appliesto:  
- Windows 10  
- Windows 11  
ms.collection: essentials-manage  
---

# Surface Support Portal overview

The Surface Support Portal simplifies device support and service management for businesses. This portal offers faster, more efficient support for Surface devices, ensuring that any issues are promptly addressed.

With the Surface Support Portal, you benefit from:

- Enhanced security with authentication processes to prevent unauthorized access.
- Access to qualified Surface technicians via chat or phone.
- The ability to track your complete audit history of exchanges, repairs, and technical support.
- Detailed warranty status, entitlements, and eligibility for advanced warranty programs.

To learn more, see [Surface Support Portal delivers significant time savings for IT admins](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-support-portal-delivers-significant-time-savings-for-it/ba-p/4242456)

:::image type="content" source="images/surface-service-repair/m365-admincenter-repair-request.png" alt-text="Screenshot of Surface Support Portal.":::

## Access Surface Support Portal

If you already have access to the portal, skip to the [Prerequisites section](#prerequisites).

### How to access Surface Support Portal

The onboarding process includes steps to validate your organization’s Microsoft tenant. If your organization doesn't already have a tenant, the instructions can help you create one, ensuring seamless access to the Surface Support Portal via the Microsoft 365 Admin Center.

1. **Select this [onboarding page](https://signup.microsoft.com/createaccount?culture=en-us&country=us&ru=https%3A%2F%2Fadmin.microsoft.com%2FAdminportal%2FHome%3Fmcapiorgid%3D%7Bmcapiorgid%7D%26accountid%3D%7Baccountid%7D%26&origin=servicesHub&scenario=skiplba)** to validate your organization’s email and domain. If your organization is already registered with Microsoft, sign in with your credentials.

   - If your organization doesn't have a Microsoft tenant, skip to **Step 2**.

    :::image type="content" source="images/portal-signin.png" alt-text="Screenshot of sign in page.":::

2. **Set up an account** – Begin the process of creating a new Microsoft account for your organization.

   - Provide your organization’s name, address, phone number, and the email address you want to associate with the account.

3. **Verify your identity** – Confirm your identity via text or call.

   - A verification code will be sent to you. Once verified, create your account credentials.

4. **Add your credentials** to access the Microsoft 365 Admin Center.

   - Save your email and password before proceeding to the next step. Select **Next** to continue.

5. **Add payment details**. This is the final step before you’re redirected to the Microsoft 365 Admin Center.

> [!NOTE]
> The payment information links with your account, but you are not charged until you purchase a product from Microsoft. The Surface Support Portal on Microsoft 365 Admin Center does not require any subscription to access Surface support and services.

6. After completing the payment information, you’ll be redirected to the Microsoft 365 Admin Center homepage. Select **Finish**.

7. Once in the Microsoft 365 Admin Center, request access to the Surface Support Portal.

   - If access is delayed or denied, you can still create support orders for your Surface devices by selecting the **Help and Support** node.

    :::image type="content" source="images/m365-admin-center.png" alt-text="Screenshot of Microsoft 365 Admin Center.":::

8. To expedite your support request, include your device serial numbers and your shipping address in the **Issue Description** field.

## Prerequisites

1. Before proceeding, you first need to configure at least one admin role. To learn more see:

- [Assign admin roles for Surface portals](surface-portal-admin-roles.md)
- [Add an admin](/microsoft-365/admin/add-users/assign-admin-roles#steps-add-an-admin)

2. To manage devices or take adavantage of the option to use Windows Autopilot, you first need to register them with the Surface Support Portal, as explained in the following section. 

## IT admin tasks in Surface Support Portal

This section includes key tasks to ensure your Surface devices remain compliant, up-to-date, and fully functional:

- [Register Surface devices](#register-surface-devices)
- [Manage Surface device warranty and coverage](#manage-surface-device-warranty-and-coverage)
- [Create and track support requests](#create-and-track-support-requests)
- [Create and track service requests for device replacement or repair](#create-and-track-service-requests-for-device-replacement-or-repair)
- [Review Administrator roles](#review-administrator-roles)
- [View related Surface IT tools](#view-related-surface-it-tools)

### Register Surface devices

Register your Surface devices through the Surface Support Portal to associate them with your organization’s tenant. This enables you to manage devices with Windows Autopilot, ensuring seamless integration into your IT infrastructure and simplifying device management.

1. **Begin new device registration:**
   - Select **Register devices** to start a new registration or request support.

2. **Add a single device:**
   - Enter the device serial number and PO (Purchase Order) number in the provided fields.
   - Select **Add** to register the device.

    :::image type="content" source="images/autopilot-registration.png" alt-text="Screenshot of registering devices for Windows Autopilot enrollment. ":::

3. **Add devices in bulk:**
   - Prepare a CSV file with two columns: **Device Serial Number** and **PO Number.** Ensure all serial numbers include leading zeros.
   - Select **Import CSV** to upload your file, or download a sample CSV template for reference.

4. **Confirm tenant details:**
   - Provide the required information, including contact email, tenant ID, and domain name.
   - These details are prepopulated from your signed-in account.

5. **Provide proof of ownership:**
   - Attach purchase receipts or invoices that include your company name and all device serial numbers listed.

6. **Finalize registration:**
   - Verify all details are correct and select **Request registration**.
   - Your registered devices are listed under **Date & Time,** **Request number,** and **State** for tracking and management.

    :::image type="content" source="images/finalize-registration.png" alt-text="Screenshot of submitting registration request.":::

### Manage Surface device warranty and coverage

Easily manage your Surface device warranties through the Surface Support Portal. You can view the coverage status of each device, track warranty timelines, and monitor the status of your service orders.

- Select **Coverage** to view devices covered under warranty, the time remaining for each device under warranty, and related details.
- Select **Warranty & service** to view the status of service orders.

### Create and track support requests

Easily submit support requests through the Surface Support Portal by providing detailed information about the issue you’re facing. The more specific your description, the faster we can help resolve your problem.

1. Select **Create support request** and describe the issue you’re experiencing.

    :::image type="content" source="images/surface-support-request.png" alt-text="Screenshot of entering a support request.":::

2. Select **Contact me** to submit your support request.

Your request will be listed under "Support requests," where you can track the status and manage any open or closed requests.

### Create and track service requests for device replacement or repair

Quickly address hardware issues by creating a service request for device replacement or repair. Additionally, you can access a complete history of your support and repair requests, giving you a comprehensive view of your device’s service history.

1. Select **Create service request** and follow the instructions. Provide a detailed description of the issue with your device or accessory.

    :::image type="content" source="images/service-request.png" alt-text="Screenshot of entering a service request for device replacement or repair.":::

2. Select **Submit** to send your service request.

### Review Administrator roles

- For details about all available admin roles, see [Assign admin roles for Surface portals](surface-portal-admin-roles.md).
- To learn more about configuring roles, see [Add an admin](/microsoft-365/admin/add-users/assign-admin-roles#steps-add-an-admin).

### View related Surface IT tools

- Select **Surface IT Tools** to access details about the latest tools, including the [Surface IT Toolkit](surface-it-toolkit.md), [Surface Diagnostics Toolkit for Business](surface-diagnostic-toolkit-business.md), and [Surface API Management Service](https://github.com/microsoft/SurfaceApiManagementService).

## Learn more

- [Surface Support Portal delivers significant time savings for IT admins](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-support-portal-delivers-significant-time-savings-for-it/ba-p/4242456)
- [Assign admin roles for Surface portals](surface-portal-admin-roles.md)
- [Surface portals overview](surface-portals.md)
- [Surface Management Portal overview](surface-management-portal.md)
- [Surface Support Portal overview](surface-support-portal.md)
- [Surface IT Toolkit](surface-it-toolkit.md)
