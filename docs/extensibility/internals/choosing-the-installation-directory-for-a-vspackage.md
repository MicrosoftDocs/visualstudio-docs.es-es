---
title: "Elija el directorio de instalaci&#243;n de un paquete VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, directorio de instalación"
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Elija el directorio de instalaci&#243;n de un paquete VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un Paquete y sus archivos auxiliares deben estar en el sistema de archivos de un usuario.  La ubicación depende de si el paquete VSPackage es administrado o no administrado, en paralelo el esquema de la versión, y la elección del usuario.  
  
## VSPackages administrados  
 Un VSPackage no administrado es un servidor COM que se puede instalar en cualquier ubicación.  La necesidad de la información de registro refleja con precisión la ubicación.  La interfaz de usuario del instalador \(UI\) debe proporcionar una ubicación predeterminada como un subdirectorio de la propiedad de ProgramFilesFolder Windows Installer.  Por ejemplo:  
  
 \[ProgramFilesFolder\] MyCompany \\MyVSPackageProduct\\V 1,0 \\  
  
 El usuario debe tener la posibilidad de cambiar el directorio predeterminado para dar servicio a usuarios que mantienen una pequeña parte de arranque y la prefieren instalar aplicaciones y herramientas en otro volumen.  
  
 Si el esquema en paralelo utiliza un VSPackage versiones, puede utilizar subdirectorios para almacenar versiones diferentes.  Por ejemplo:  
  
 \[ProgramFilesFolder\] MyCompany \\MyVSPackageProduct\\V 1,0 \\ 2002 \\  
  
 \[ProgramFilesFolder\] MyCompany \\MyVSPackageProduct\\V 1,0 \\ 2003 \\  
  
 \[ProgramFilesFolder\] MyCompany \\MyVSPackageProduct\\V 1,0 \\ 2005 \\  
  
## VSPackages administrado  
 VSPackages administrado también se puede instalar en cualquier ubicación.  Sin embargo, siempre debería instalarlos a la caché global de ensamblados \(GAC\) para reducir los tiempos de carga de ensamblado.  Porque VSPackages administrado siempre fuerte\-se llama a los ensamblados, instalarlos en la GAC significan que la comprobación de firmas con nombre seguro toma solo en tiempo de instalación.  los ensamblados con nombre seguro instalados en otra parte del sistema de archivos deben tener las firmas comprobar cada vez que se cargan.  Al instalar VSPackages administrado en la GAC, utilice el modificador **\/assembly** de herramienta de regpkg para escribir las entradas del Registro que señalan al nombre seguro del ensamblado.  
  
 Si instala VSPackages administrado en una ubicación distinta de la GAC, siga el consejo anterior especificado para VSPackages administrados para elegir jerarquías de directorio.  Utilice el modificador **\/codebase** de herramienta de regpkg para escribir las entradas del Registro que señalan a la ruta de acceso del ensamblado de VSPackage.  
  
 Para obtener más información, vea [Registrar y anular el registro VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## Archivos DLL satélite  
 Por convención, los archivos DLL satélite de VSPackage — que contienen recursos para una configuración regional concreta \(están ubicados en subdirectorios del directorio de VSPackage.  Los subdirectorios corresponden a los valores del identificador de configuración regional \(LCID\).  
  
 [Administración de VSPackages](../../extensibility/managing-vspackages.md) indica que las entradas de Registro controlan donde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] busca realmente DLL satélite de un Paquete.  Sin embargo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] intenta cargar un archivo DLL satélite en un subdirectorio denominado por un valor LCID, en el orden siguiente:  
  
1.  LCID predeterminado \(VS LCID por ejemplo \\1033 for English\)  
  
2.  LCID predeterminado con el sublenguaje predeterminado.  
  
3.  Valor predeterminado del sistema LCID.  
  
4.  Valor predeterminado del sistema LCID con el sublenguaje predeterminado.  
  
5.  EE.UU.  inglés \(.  \\ 1033 o.  \\ 0x409\).  
  
 Si el paquete VSPackage DLL incluye recursos y los puntos de entrada del Registro de SatelliteDll \\DllName, a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] intenta cargarlos en el orden anterior.  
  
## Vea también  
 [Elegir entre VSPackages compartido y su versión](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Administración de VSPackages](../../extensibility/managing-vspackages.md)   
 [Managed Package Registration](http://msdn.microsoft.com/es-es/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)