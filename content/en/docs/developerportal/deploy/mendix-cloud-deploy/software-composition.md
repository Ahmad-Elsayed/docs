---
title: "Software Composition"
url: /developerportal/deploy/software-composition/
description: "Describes the Software Composition page in the Developer Portal."
tags: ["developer portal", "deployment", "software composition"]
weight: 80
no_list: true
---

{{% alert color="warning" %}}This feature is in beta. For more information, see [Beta Releases](/releasenotes/beta-features/). {{% /alert %}}

## 1 Introduction

From the **Software Composition** page in the Developer Portal, you can drill down and view the components of each app environment. Besides, you can view the usage of components across your deployed packages under [All Components](#all-components), where standard marketplace modules, widgets, java libraries, and Mendix runtime version are available. In the event when a security vulnerability is detected, [Component Usage](#component-usage) can help you assess the impact radius and take action accordingly.

Make sure that you meet the following prerequisites:

* Component details and related actions are only available for apps made with Mendix versions [9.24.14](/releasenotes/studio-pro/9.24/#92414) and above or Mendix versions [10.5.0](/releasenotes/studio-pro/10.5/#1050) and above when they are deployed to Mendix Cloud or Cloud Dedicated. Make sure that you upgrade to one of these versions to see component information reflected on this page.
* You have to create and deploy new deployment packages in order to get the software composition information populated on this page. For more information, see the [How Components Are Identified](#how-components-are-identified) section.

### 1.1 How Components Are Identified {#how-components-are-identified}

Components are identified in the following manner:

First, when a new deployment package is created via the Developer Portal with the compatible Mendix Runtime version, a software bill of material (SBOM) is generated along with it. The log details can be viewed by clicking **View build output** in the deployment package details in the Developer Portal.

Then, when this deployment package is deployed to an environment, the information about the components becomes available on the **Software Composition** page in the Developer Portal.

## 2 Overview {#overview}

On the **Overview** tab, you can see a list of all the deployed packages and their environments.

Above the list, you can use the search box to search for information in the list. Next to the search box, you can filter apps by selecting the environment type or the Mendix Runtime version. You can click {{% icon name="office-sheet" %}}**Export all** on the right side above the list to export all the information in the list to an Excel file.

The list contains the following information:

* **Deployment Package**: This is the name of the deployment package. Click this opens the [Deployment Package Summary](#deployment-package-summary) page, if it is available.
* **Technical Contact**: This shows the Technical Contact of the app.
* **Environment**: This is the name of the environment.
* **Production**: This shows whether the deployment package is deployed in the production environment.
* **Runtime**: This shows the Mendix Runtime version.
* **Version**: This shows the version of the deployment package on this app environment.
* **Action**: Clicking the {{% icon name="download-bottom" %}} icon to download the software bill of materials (SBOM). For more information, see [Downloading the Software Bill of Materials](#download-software-bill-of-materials).
* {{% icon name="view" %}}: You can customize the columns of the list by clicking the {{% icon name="view" %}} icon and adjusting the selection of the check boxes.

To export the information of selected items in the list to an Excel file, select the check boxes of the items in the list, and then click {{% icon name="office-sheet" %}}**Selection Export to Excel** that appears at the bottom of the page.

### 2.1 Downloading the Software Bill of Materials {#download-software-bill-of-materials}

A software bill of materials is a vehicle to share information on the inventory of a software component. It contains a description about the Mendix app and the components (dependencies) put into it. 

{{% alert color="info" %}}The software bill of materials for all the components is stored in the `vendorlib-sbom.json` file in the `vendorlib` library in the app directory. For more information, see the [Dependency Synchronization](/refguide/managed-dependencies/#dependency-synchronization) section in *Managed Dependencies*.{{% /alert %}}

In the list on the **Overview** tab, you can click {{% icon name="download-bottom" %}} icon in the **Action** column to download the software bill of materials (SBOM). The current version of the SBOM contains standard marketplace modules, widgets, java libraries, and the Mendix runtime version. The SBOM is a *.json* file in the CycloneDX format.

Currently, the SBOM has the following known limitations:

* Add-on modules, solution modules, solutions, and npms are not available as SBOM components currently. This will be improved in future versions.
* Components which are not imported via the Marketplace are not visible in the SBOM.
* The metadata of private Marketplace components and the metadata of widgets imported as a part of a module are limited.
* No dependency information between components is available in the SBOM, except for the java dependencies available for SBOMs created from Studio Pro versions 10.5.0 and above.

### 2.2 Deployment Package Summary {#deployment-package-summary}

On the **Overview** tab, if you click **View Details** for a deployment package in the list, the **Deployment Package Summary** page opens. 

On the top of the page, you can find the name of the deployment package, the environment name, the Mendix Runtime version, the Technical Contact, the Mendix Runtime version, the version of the deployment package, and whether the deployment package is deployed in a product environment.

For details on the information in the list and how to search, filter, and export information in the list, see the [All Components](#all-components) section.

## 3 All Components {#all-components}

The **All Components** tab gives an overview of all the components used across your deployment packages. 

{{% alert color="info" %}}This only includes the newly-created apps for which a deployment package and hence a software bill of materials is available.{{% /alert %}}

Above the list, you can use the search box to search for a component. Next to the search box, you can filter components by selecting the component type. You can click {{% icon name="office-sheet" %}}**Export all to Excel** on the right side above the list to export all the information in the list to an Excel file.

The list shows the following information about the component:

* **Component**: This is the name of the component.
* **Version**: This is the component version.
* **Type**: This shows the type of the component.
* {{% icon name="view" %}}: You can customize the columns of the list by clicking the {{% icon name="view" %}} icon and adjusting the selection of the check boxes.
* **View details**: Click this opens the [Component Usage](#component-usage) page.

To export the information of selected items in the list to an Excel file, select the check boxes of the items in the list, and then click {{% icon name="office-sheet" %}}**Selection Export to Excel** that appears at the bottom of the page.

### 3.1 Component Usage {#component-usage}

On the **All Components** tab, if you click **View details** for an item, the **Component Usage** page opens. This page lists the environments where the selected component is being used. If a security vulnerabilities is found in one of the components, then the component usage tab can be used to assess the impact radius. The relevant Technical Contacts can be informed to take the necessary remediation actions.

On the top of the page, you can find the component name, the component version, and the component type. 

For details on the information in the list and how to search, filter, and export information in the list, see the [Overview](#overview) section.