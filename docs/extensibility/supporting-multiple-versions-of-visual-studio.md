---
title: "Compatibilidad con varias versiones de Visual Studio | Microsoft Docs"
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
  - "Visual Studio, la compatibilidad con múltiples versiones"
  - "VSPackages, compatibilidad en paralelo"
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Compatibilidad con varias versiones de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El término *side\-by\-side* significa que puede instalar y mantener varias versiones de un producto en el mismo equipo. Para VSPackages, que significa que un usuario puede tener varias versiones de Visual Studio instaladas en el mismo equipo. Sin embargo, no puede tener versiones en paralelo de su VSPackages cargado en una única versión de Visual Studio.  
  
 Antes de realizar el VSPackage que se pueda cargar en paralelo para las versiones de Visual Studio, considere lo siguiente:  
  
-   Debe determinar qué estrategia de implementación en paralelo que desea seguir.  
  
     Para obtener más información, consulta [Elegir entre VSPackages compartido y su versión](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   Los formatos de archivo de solución y proyecto deben ajustarse a su estrategia de implementación.  
  
     Para obtener más información, vea [Actualizar proyectos personalizados](../misc/upgrading-custom-projects.md) y [Registrar extensiones de nombre de archivo para las implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   El instalador debe controlar la estrategia de implementación para que los componentes y también los componentes compartidos por todas las versiones están correctamente instalados y registrados.  
  
     Para obtener más información, consulte [Instalación de VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) y [Administración de componentes](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Instalar una versión de Visual Studio, también instala una versión correspondiente de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Por ejemplo, la instalación de Visual Studio 2010 y Visual Studio 2012 en el mismo equipo también instala las versiones 4.0 y 4.5 de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], respectivamente.  
  
## En esta sección  
 [Elegir entre VSPackages compartido y su versión](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Explica cómo resolver problemas en su VSPackage.  
  
 [Registrar extensiones de nombre de archivo para las implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Describe cómo el VSPackage puede registrar las asociaciones de archivo en un escenario en paralelo.  
  
## Secciones relacionadas  
 [Instalar VSPackages](../misc/installing-vspackages.md)  
 Describe cómo compilar e instalar VSPackages y cómo admitir usuarios que ejecutan varias versiones de Visual Studio al mismo tiempo.