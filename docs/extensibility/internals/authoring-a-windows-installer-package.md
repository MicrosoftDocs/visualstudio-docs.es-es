---
title: "Creación de un paquete de Windows Installer | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5f646e2234adf0eb0117f154838b15d7b3aa200e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="authoring-a-windows-installer-package"></a>Creación de un paquete de Windows Installer
Unidades de datos del modelo de Windows Installer. En lugar de escribir una secuencia de comandos de procedimientos para copiar archivos y escribir entradas del registro, por ejemplo, crea filas y columnas en tablas de base de datos que contienen datos de archivos y del registro.  
  
## <a name="database-entries"></a>Entradas de la base de datos  
 Para instalar un paquete VSPackage, un paquete de Windows Installer debe contener entradas de la base de datos para llevar a cabo las siguientes tareas:  
  
-   Busque en el sistema para encontrar las versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el paquete de VS es compatible con (con las tablas de Windows Installer que incluyan AppSearch, CompLocator, RegLocator, DrLocator y firma).  
  
-   Cancelar la instalación si ninguna versión compatible de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está instalado o si no se cumple otro requisito de sistema de VSPackage (con la tabla LaunchCondition).  
  
-   Instale el paquete de VS y los archivos dependientes (mediante el directorio, componente y tablas de archivos).  
  
-   Agregar información apropiada para el VSPackage en el registro (con la tabla del registro).  
  
-   Integrar el VSPackage en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mediante una llamada a **devenv.exe /setup** (con la tabla CustomAction).  
  
 Para obtener más información, consulte [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Herramientas de configuración  
 Una variedad de herramientas de configuración de aplicaciones de terceros proporcionan un entorno de desarrollo para paquetes de Windows Installer. Dos herramientas gratuitas son los siguientes:  
  
-   InstallShield Limited Edition  
  
     Puede obtener una versión limitada de InstallShield a través de Visual Studio **nuevo proyecto** cuadro de diálogo. Expanda **otros tipos de proyectos** y, a continuación, seleccione **el programa de instalación e implementación**. Seleccione la plantilla de InstallShield.  
  
-   Conjunto de herramientas de Windows Installer XML  
  
     El conjunto de herramientas compila paquetes de Windows Installer desde archivos de origen XML. El conjunto de herramientas es un proyecto de código abierto de Microsoft. Puede descargar el código fuente y los archivos ejecutables de [http://sourceforge.net/projects/wix](http://sourceforge.net/projects/wix).  
  
 Para los productos comerciales que se integran en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mediante el uso de la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], consulte [http://visualstudiogallery.com](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Vea también  
 [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)