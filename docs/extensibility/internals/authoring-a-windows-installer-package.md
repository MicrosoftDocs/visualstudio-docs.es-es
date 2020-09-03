---
title: Crear un paquete de Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d30c0e2b3b375e6e0efedddd3a017fbfb8646a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710040"
---
# <a name="author-a-windows-installer-package"></a>Crear un paquete de Windows Installer
Data impulsa el modelo de Windows Installer. En lugar de escribir un script de procedimientos para copiar archivos y escribir entradas del registro, por ejemplo, se crean filas y columnas en las tablas de base de datos que contienen datos de archivos y del registro.

## <a name="database-entries"></a>Entradas de base de datos
Para instalar un VSPackage, un paquete de Windows Installer debe contener entradas de base de datos para realizar las tareas siguientes:

- Busque en el sistema para encontrar las versiones del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage que admite (mediante Windows Installer tablas que incluyan AppSearch, CompLocator, RegLocator, DrLocator y Signature).

- Cancele la instalación si no se ha instalado ninguna versión compatible de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o si no se cumple otro requisito del sistema del VSPackage (mediante la tabla LaunchCondition).

- Instale el VSPackage y los archivos dependientes (mediante el directorio, el componente y las tablas de archivo).

- Agregue la información adecuada para el VSPackage al registro (mediante la tabla del registro).

- Integre el VSPackage en llamando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **devenv.exe/Setup** (mediante la tabla CustomAction).

Para obtener más información, vea [Windows Installer](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Herramientas de instalación
Una variedad de herramientas de instalación de terceros proporciona un entorno de desarrollo para Windows Installer paquetes. Están disponibles las siguientes herramientas gratuitas:

- InstallShield Limited Edition

   Puede obtener una versión limitada de InstallShield mediante el cuadro de diálogo **nuevo proyecto** de Visual Studio. Expanda **otros tipos de proyecto** y, a continuación, seleccione **instalación e implementación**. Seleccione la plantilla de InstallShield.

- Conjunto de herramientas de Windows Installer XML

   El conjunto de herramientas de Windows Installer XML (WiX) crea paquetes de Windows Installer a partir de archivos de origen XML. El conjunto de herramientas de WiX es un proyecto de código abierto de Microsoft. Puede descargar el código fuente y los ejecutables del [conjunto de herramientas de Wix](https://sourceforge.net/projects/wix/).

   Para los productos comerciales que se integran en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mediante [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , consulte [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Vea también
- [Instale VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
