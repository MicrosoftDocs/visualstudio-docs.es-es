---
title: Instalación de VSPackages con Windows Installer ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2eb90dbffa9f04cd17afa70d2bdfc59205bc99cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707461"
---
# <a name="installing-vspackages-with-windows-installer"></a>Instalación de VSPackages con Windows Installer
La integración de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage en requiere algo más que copiar archivos en el equipo de un usuario. El instalador de VSPackage debe instalar el VSPackage y sus [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]archivos dependientes, y registrarlos e integrarlos en . El VSPackage puede aprovechar las características de integración, como mostrar un icono en la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pantalla de presentación y Acerca del cuadro de diálogo.

 Los archivos de Microsoft Windows Installer son la forma recomendada de distribuir los VSPackages. Los paquetes de Windows Installer fáciles de usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]se pueden ejecutar en cualquier sistema operativo Windows compatible con . Para obtener más información, consulte [Windows Installer](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).

## <a name="in-this-section"></a>En esta sección
- [Datos básicos de Windows Installer](../../extensibility/internals/windows-installer-basics.md)

 Proporciona información general sobre Windows Installer.

- [Escenarios de instalación de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

 Describe diferentes maneras en las que puede admitir instalaciones [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]en paralelo de los VSPackages y .

- [Creación de un paquete de Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)

 Proporciona información general de los pasos típicos que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]siguen los instaladores para instalar e integrar correctamente VSPackages en .

- [Detección de requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md)

 Describe cómo un instalador [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] puede detectar y sus componentes y cancelar la instalación si no se cumplen los requisitos de VSPackage.

- [Administración de componentes](../../extensibility/internals/component-management.md)

 Describe cómo desarrollar un instalador que mantenga la integridad de las versiones anteriores del producto.

- [Selección del directorio de instalación de un VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Resume las opciones para localizar VSPackages.

- [Registro de VSPackage](../../extensibility/internals/vspackage-registration.md)

 Describe cómo se registran los VSPackages en el momento de la instalación y por qué el autorregistro es una mala idea.

- [Implementación de tipos de proyecto](../../extensibility/internals/deploying-project-types.md)

 Describe cómo usar el nuevo agregador de tipo de proyecto para los tipos de proyecto de código administrado.

- [Generación de información del Registro para un instalador](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 Explica cómo usar RegPkg.exe para generar un manifiesto de registro para un VSPackage administrado.

- [Comandos que se deben ejecutar después de la instalación](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 Explica cómo ejecutar comandos posteriores a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]la instalación para integrar VSPackages en .

- [Desinstalación de un VSPackage con Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 Describe los pasos que debe realizar el instalador cuando los usuarios desinstalan el VSPackage.
