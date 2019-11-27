---
title: Crear un paquete de Windows Installer | Microsoft Docs
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

Data impulsa el modelo de Windows Installer. En lugar de escribir un script de procedimientos para copiar archivos y escribir entradas del registro, por ejemplo, se crean filas y columnas en las tablas de base de datos que contienen datos de archivos y del registro.  
  
## <a name="database-entries"></a>Entradas de la base de datos  
 Para instalar un VSPackage, un paquete de Windows Installer debe contener entradas de base de datos para realizar las tareas siguientes:  
  
- Busque en el sistema para buscar las versiones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que admite el VSPackage (con Windows Installer tablas que incluyen AppSearch, CompLocator, RegLocator, DrLocator y Signature).  
  
- Cancele la instalación si no se instala ninguna versión compatible de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o si no se cumple otro requisito del sistema del VSPackage (mediante la tabla LaunchCondition).  
  
- Instale el VSPackage y los archivos dependientes (mediante el directorio, el componente y las tablas de archivo).  
  
- Agregue la información adecuada para el VSPackage al registro (mediante la tabla del registro).  
  
- Integre el VSPackage en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] llamando a **devenv. exe/setup** (mediante la tabla CustomAction).  
  
  Para obtener más información, vea [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Herramientas de instalación  
 Una variedad de herramientas de instalación de terceros proporciona un entorno de desarrollo para Windows Installer paquetes. Dos herramientas gratuitas son las siguientes:  
  
- InstallShield Limited Edition  
  
   Puede obtener una versión limitada de InstallShield mediante el cuadro de diálogo **nuevo proyecto** de Visual Studio. Expanda **otros tipos de proyecto** y, a continuación, seleccione **instalación e implementación**. Seleccione la plantilla de InstallShield.  
  
- Conjunto de herramientas de Windows Installer XML  
  
   El conjunto de herramientas crea paquetes de Windows Installer a partir de archivos de código fuente XML. El conjunto de herramientas es un proyecto de código abierto de Microsoft. Puede descargar el código fuente y los ejecutables desde [http://sourceforge.net/projects/wix](https://sourceforge.net/projects/wix/).  
  
  Para los productos comerciales que se integran en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mediante el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], consulte [https://marketplace.visualstudio.com/](https://marketplace.visualstudio.com/).  
  
## <a name="see-also"></a>Vea también  
 [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
