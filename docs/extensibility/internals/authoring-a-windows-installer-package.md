---
title: Creación de un paquete de Windows Installer ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710040"
---
# <a name="author-a-windows-installer-package"></a>Crear un paquete de Windows Installer
Los datos controlan el modelo de Windows Installer. En lugar de escribir un script de procedimiento para copiar archivos y escribir entradas del Registro, por ejemplo, se escriben filas y columnas en tablas de base de datos que contienen datos de archivo y registro.

## <a name="database-entries"></a>Entradas de base de datos
Para instalar un VSPackage, un paquete de Windows Installer debe contener entradas de base de datos para realizar las siguientes tareas:

- Busque en el sistema [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para buscar las versiones de los soportes de VSPackage (mediante tablas de Windows Installer que incluyen AppSearch, CompLocator, RegLocator, DrLocator y Signature).

- Cancele la instalación si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no se instala ninguna versión compatible de o si no se cumple otro requisito del sistema del VSPackage (mediante la tabla LaunchCondition).

- Instale el VSPackage y los archivos dependientes (mediante el directorio, el componente y las tablas de archivos).

- Agregue la información adecuada para el VSPackage al registro (mediante la tabla del Registro).

- Integre el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage mediante una llamada a **devenv.exe /setup** (mediante la tabla CustomAction).

Para obtener más información, consulte [Windows Installer](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Herramientas de configuración
Una variedad de herramientas de instalación de terceros proporcionan un entorno de desarrollo para paquetes de Windows Installer. Están disponibles las siguientes herramientas gratuitas:

- InstallShield edición limitada

   Puede obtener una versión limitada de InstallShield a través del cuadro de diálogo **Nuevo proyecto** de Visual Studio. Expanda **Otros tipos de proyecto** y, a continuación, seleccione Configuración e **implementación**. Seleccione la plantilla InstallShield.

- Conjunto de herramientas XML de Windows Installer

   El conjunto de herramientas XML (WiX) de Windows Installer compila paquetes de Windows Installer a partir de archivos de origen XML. El conjunto de herramientas WiX es un proyecto de código abierto de Microsoft. Puede descargar el código fuente y los ejecutables desde el conjunto de [herramientas Wix.](https://sourceforge.net/projects/wix/)

   Para los productos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comerciales que [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]se integran mediante el archivo , vea [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Vea también
- [Instalar VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
