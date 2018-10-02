---
title: Creación de un paquete de Windows Installer | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a9b56ea9120e3cbee18d8018420a94748dc52eec
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566059"
---
# <a name="authoring-a-windows-installer-package"></a>Creación de un paquete de Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [creación de un paquete de Windows Installer](https://docs.microsoft.com/visualstudio/extensibility/internals/authoring-a-windows-installer-package).  
  
El modelo de Windows Installer de las unidades de datos. En lugar de escribir un script de procedimiento para copiar archivos y escribir entradas del registro, por ejemplo, crea filas y columnas en tablas de base de datos que contienen datos de archivos y del registro.  
  
## <a name="database-entries"></a>Entradas de la base de datos  
 Para instalar un paquete VSPackage, un paquete de Windows Installer debe contener las entradas de la base de datos para llevar a cabo las siguientes tareas:  
  
-   Busque en el sistema para encontrar las versiones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el paquete de VS es compatible con (con las tablas de Windows Installer que incluyan AppSearch, CompLocator, RegLocator, DrLocator y firma).  
  
-   Cancelar la instalación si ninguna versión compatible de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] está instalado o si no se cumple otro requisito de sistema de VSPackage (con la tabla LaunchCondition).  
  
-   Instale el paquete VSPackage y los archivos dependientes (con el directorio, componente y tablas de archivos).  
  
-   Agregue la información adecuada para el VSPackage en el registro (con la tabla del registro).  
  
-   Integrar el VSPackage en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mediante una llamada a **devenv.exe /setup** (con la tabla CustomAction).  
  
 Para obtener más información, consulte [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Herramientas de instalación  
 Una variedad de herramientas del programa de instalación de aplicaciones de terceros proporcionan un entorno de desarrollo para paquetes de Windows Installer. Dos herramientas gratuitas son los siguientes:  
  
-   InstallShield Limited Edition  
  
     Puede obtener una versión limitada de InstallShield a través de Visual Studio **nuevo proyecto** cuadro de diálogo. Expanda **otros tipos de proyectos** y, a continuación, seleccione **instalación e implementación**. Seleccione la plantilla de InstallShield.  
  
-   Conjunto de herramientas de Windows Installer XML  
  
     El conjunto de herramientas compila paquetes de Windows Installer desde archivos de origen XML. El conjunto de herramientas es un proyecto de código abierto de Microsoft. Puede descargar el código fuente y los archivos ejecutables de [ http://sourceforge.net/projects/wix ](http://sourceforge.net/projects/wix).  
  
 Para los productos comerciales que se integran en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utilizando el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], consulte [ http://visualstudiogallery.com ](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Vea también  
 [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

