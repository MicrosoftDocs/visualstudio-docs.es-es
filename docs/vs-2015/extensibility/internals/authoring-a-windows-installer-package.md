---
title: Authoring a Windows Installer Package | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58529dabbb52ceb751c67be24beb1d21285a1de6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301139"
---
# <a name="authoring-a-windows-installer-package"></a>Creación de un paquete de Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Data drives the Windows Installer model. Rather than writing a procedural script to copy files and write registry entries, for example, you author rows and columns in database tables that contain file and registry data.  
  
## <a name="database-entries"></a>Entradas de la base de datos  
 To install a VSPackage, a Windows Installer package must contain database entries to perform the following tasks:  
  
- Search the system to locate the versions of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] your VSPackage supports (using Windows Installer tables that include AppSearch, CompLocator, RegLocator, DrLocator, and Signature).  
  
- Cancel the installation if no supported version of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] is installed or if another system requirement of the VSPackage is not met (using the LaunchCondition table).  
  
- Install the VSPackage and dependent files (using the directory, component, and file tables).  
  
- Add appropriate information for the VSPackage to the registry (using the Registry table).  
  
- Integrate the VSPackage in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] by calling **devenv.exe /setup** (using the CustomAction table).  
  
  For more information, see [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Setup Tools  
 A variety of third-party setup tools provide a development environment for Windows Installer packages. Two free tools are the following:  
  
- InstallShield Limited Edition  
  
   You can get a limited version of InstallShield through the Visual Studio **New Project** dialog. Expand **Other Project Types** and then select **Setup and Deployment**. Select the InstallShield template.  
  
- Conjunto de herramientas de Windows Installer XML  
  
   The Toolset builds Windows Installer packages from XML source files. The Toolset is a Microsoft open-source project. You can download the source code and executables from [http://sourceforge.net/projects/wix](https://sourceforge.net/projects/wix/).  
  
  For commercial products that integrate into [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] by using the [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], see [https://marketplace.visualstudio.com/](https://marketplace.visualstudio.com/).  
  
## <a name="see-also"></a>Vea también  
 [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
