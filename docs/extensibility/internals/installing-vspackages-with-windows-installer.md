---
title: Instalación de VSPackages con Windows Installer | Microsoft Docs
description: Obtenga información sobre cómo usar el Microsoft Windows Installer para instalar un VSPackage y sus archivos dependientes, y registrarlos e integrarlos en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3ab4493d1d3acce3ad28c834136d25264a74180
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839825"
---
# <a name="installing-vspackages-with-windows-installer"></a>Instalación de VSPackages con Windows Installer
La integración del VSPackage en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] requiere más que copiar archivos en el equipo de un usuario. El instalador de VSPackage debe instalar el VSPackage y sus archivos dependientes, y registrarlos e integrarlos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . El VSPackage puede aprovechar las características de integración, como mostrar un icono en la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pantalla de presentación y en el cuadro de diálogo acerca de.

 Microsoft Windows Installer archivos son la manera recomendada de distribuir los VSPackages. Los paquetes de Windows Installer fáciles de usar se pueden ejecutar en cualquier sistema operativo Windows compatible con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Para obtener más información, vea [Windows Installer](/previous-versions/2kt85ked(v=vs.120)).

## <a name="in-this-section"></a>En esta sección
- [Datos básicos de Windows Installer](../../extensibility/internals/windows-installer-basics.md)

 Proporciona información general sobre el Windows Installer.

- [Escenarios de instalación de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

 Describe las diferentes maneras en las que puede admitir instalaciones en paralelo de sus VSPackages y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Creación de un paquete de Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)

 Proporciona información general de los instaladores de pasos típicos que se indican a continuación para instalar e integrar correctamente VSPackages en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Detección de requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md)

 Describe cómo un instalador puede detectar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y sus componentes y cancelar el programa de instalación si no se cumplen los requisitos de VSPackage.

- [Administración de componentes](../../extensibility/internals/component-management.md)

 Describe cómo desarrollar un instalador que mantendrá la integridad de las versiones anteriores del producto.

- [Selección del directorio de instalación de un VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Resume las opciones para buscar VSPackages.

- [Registro de VSPackage](../../extensibility/internals/vspackage-registration.md)

 Describe cómo se registran los VSPackages en el momento de la instalación y por qué no es una buena idea.

- [Implementación de tipos de proyecto](../../extensibility/internals/deploying-project-types.md)

 Describe cómo usar el nuevo agregador de tipo de proyecto para los tipos de proyecto de código administrado.

- [Generación de información del Registro para un instalador](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 Explica cómo usar RegPkg.exe para generar un manifiesto de registro para un VSPackage administrado.

- [Comandos que se deben ejecutar después de la instalación](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 Explica cómo ejecutar comandos posteriores a la instalación para integrar los VSPackages en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Desinstalación de un VSPackage con Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 Describe los pasos que debe realizar el instalador cuando los usuarios desinstalan el VSPackage.