---
title: "Creaci&#243;n de un paquete de Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "archivos .msi, VSPackages"
  - "archivos MSI, VSPackages"
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Creaci&#243;n de un paquete de Windows Installer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Unidades de datos del modelo de Windows Installer. En lugar de escribir una secuencia de comandos de procedimientos para copiar archivos y escribir entradas del registro, por ejemplo, se crean filas y columnas en tablas de base de datos que contienen datos de archivos y del registro.  
  
## Entradas de la base de datos  
 Para instalar un paquete VSPackage, un paquete de Windows Installer debe contener entradas de base de datos para llevar a cabo las siguientes tareas:  
  
-   Busque en el sistema para encontrar las versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el VSPackage admite \(con las tablas de Windows Installer que incluyen AppSearch, CompLocator, RegLocator, DrLocator y firma\).  
  
-   Cancelar la instalación si ninguna versión compatible de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está instalado o si no se cumple otro requisito del sistema de VSPackage \(con la tabla LaunchCondition\).  
  
-   Instalar el paquete VSPackage y archivos dependientes \(con el directorio, componente y tablas de archivos\).  
  
-   Agregar la información apropiada para el VSPackage al registro \(con la tabla del registro\).  
  
-   Integrar VSPackage en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mediante una llamada a **devenv.exe \/setup** \(con la tabla CustomAction\).  
  
 Para obtener más información, consulte [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## Herramientas de instalación  
 Una variedad de herramientas de instalación de terceros proporcionan un entorno de desarrollo de paquetes de Windows Installer. Dos herramientas gratuitas son los siguientes:  
  
-   InstallShield Limited Edition  
  
     Puede obtener una versión limitada de InstallShield a través de Visual Studio **nuevo proyecto** cuadro de diálogo. Expanda **otros tipos de proyectos** y, a continuación, seleccione **instalación e implementación**. Seleccione la plantilla de InstallShield.  
  
-   Conjunto de herramientas de Windows Installer XML  
  
     El conjunto de herramientas crea paquetes de Windows Installer desde archivos de origen XML. El conjunto de herramientas es un proyecto de código abierto de Microsoft. Puede descargar el código fuente y los archivos ejecutables de [http:\/\/sourceforge.net\/projects\/wix](http://sourceforge.net/projects/wix).  
  
 Para los productos comerciales que se integran en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizando el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], consulte [http:\/\/visualstudiogallery.com](http://visualstudiogallery.com/).  
  
## Vea también  
 [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)