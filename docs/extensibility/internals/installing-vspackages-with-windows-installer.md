---
title: Instalación de VSPackages con Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e0efb1b5c45595383f62d08399906cbb1b546479
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827840"
---
# <a name="installing-vspackages-with-windows-installer"></a>Instalación de VSPackages con Windows Installer
Integrar el VSPackage en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] requiere algo más que copiar los archivos al equipo de un usuario. Instalador de su VSPackage debe instalar el paquete VSPackage y sus archivos dependientes y registrar e integrarlos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. El VSPackage puede aprovechar las características de integración, como mostrar un icono en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cuadro de diálogo acerca de pantalla de presentación.  
  
 Archivos de Microsoft Windows Installer son la manera recomendada para distribuir los VSPackages. Pueden ejecutar paquetes de Windows Installer para uso en cualquier sistema operativo de Windows compatible con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulte [Windows Installer](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>En esta sección  
 [Datos básicos de Windows Installer](../../extensibility/internals/windows-installer-basics.md)  
 Proporciona información general de Windows Installer.  
  
 [Escenarios de instalación de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Describe diferentes maneras puede admitir las instalaciones en paralelo de ambos los VSPackages y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Creación de un paquete de Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Proporciona información general sobre los pasos típicos instaladores seguir para instalar correctamente y cómo integrar VSPackages en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Detección de requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md)  
 Describe cómo puede detectar un instalador [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y sus componentes y cancelar la instalación si no se cumplen los requisitos de VSPackage.  
  
 [Administración de componentes](../../extensibility/internals/component-management.md)  
 Describe cómo desarrollar a un instalador que mantendrá la integridad de las versiones anteriores del producto.  
  
 [Selección del directorio de instalación de un VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Resume las opciones para la localización de VSPackages.  
  
 [Registro de VSPackage](../../extensibility/internals/vspackage-registration.md)  
 Describe cómo se registran los VSPackages en tiempo de instalación y registro automático de por qué es una mala idea.  
  
 [Implementación de tipos de proyecto](../../extensibility/internals/deploying-project-types.md)  
 Describe cómo usar el nuevo agregador de tipo de proyecto para los tipos de proyecto de código administrado.  
  
 [Cómo: Generar información del registro para un instalador](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Se explica cómo usar RegPkg.exe para generar un manifiesto de registro de un VSPackage administrado.  
  
 [Comandos que se deben ejecutar después de la instalación](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Explica cómo ejecutar los comandos posteriores a la instalación para integrar los VSPackages en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Desinstalación de un paquete VSPackage con Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Describe los pasos que debe ejecutar el instalador cuando los usuarios desinstalan el VSPackage.  