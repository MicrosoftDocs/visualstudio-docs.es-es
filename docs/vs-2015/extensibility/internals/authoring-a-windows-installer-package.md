---
title: Creación de un paquete de Windows Installer | Microsoft Docs
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
ms.openlocfilehash: 30c941fd4f3c281dfe363d284a559bafe055451c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "59002812"
---
# <a name="authoring-a-windows-installer-package"></a>Creación de un paquete de Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El modelo de Windows Installer de las unidades de datos. En lugar de escribir un script de procedimiento para copiar archivos y escribir entradas del registro, por ejemplo, crea filas y columnas en tablas de base de datos que contienen datos de archivos y del registro.  
  
## <a name="database-entries"></a>Entradas de la base de datos  
 Para instalar un paquete VSPackage, un paquete de Windows Installer debe contener las entradas de la base de datos para llevar a cabo las siguientes tareas:  
  
- Busque en el sistema para encontrar las versiones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el paquete de VS es compatible con (con las tablas de Windows Installer que incluyan AppSearch, CompLocator, RegLocator, DrLocator y firma).  
  
- Cancelar la instalación si ninguna versión compatible de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] está instalado o si no se cumple otro requisito de sistema de VSPackage (con la tabla LaunchCondition).  
  
- Instale el paquete VSPackage y los archivos dependientes (con el directorio, componente y tablas de archivos).  
  
- Agregue la información adecuada para el VSPackage en el registro (con la tabla del registro).  
  
- Integrar el VSPackage en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mediante una llamada a **devenv.exe /setup** (con la tabla CustomAction).  
  
  Para obtener más información, consulte [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Herramientas de instalación  
 Una variedad de herramientas del programa de instalación de aplicaciones de terceros proporcionan un entorno de desarrollo para paquetes de Windows Installer. Dos herramientas gratuitas son los siguientes:  
  
- InstallShield Limited Edition  
  
   Puede obtener una versión limitada de InstallShield a través de Visual Studio **nuevo proyecto** cuadro de diálogo. Expanda **otros tipos de proyectos** y, a continuación, seleccione **instalación e implementación**. Seleccione la plantilla de InstallShield.  
  
- Conjunto de herramientas de Windows Installer XML  
  
   El conjunto de herramientas compila paquetes de Windows Installer desde archivos de origen XML. El conjunto de herramientas es un proyecto de código abierto de Microsoft. Puede descargar el código fuente y los archivos ejecutables de [ http://sourceforge.net/projects/wix ](http://sourceforge.net/projects/wix).  
  
  Para los productos comerciales que se integran en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utilizando el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], consulte [ https://marketplace.visualstudio.com/ ](https://marketplace.visualstudio.com/).  
  
## <a name="see-also"></a>Vea también  
 [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
