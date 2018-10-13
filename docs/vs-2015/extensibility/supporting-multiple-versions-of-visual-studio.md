---
title: Compatibilidad con varias versiones de Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f68da8f7e397afef82c138af7d5228fe658dbb4e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192626"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Compatibilidad con varias versiones de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El término *side-by-side* significa que puede instalar y mantener varias versiones de un producto en el mismo equipo. Para los paquetes VSPackage, que significa que un usuario puede tener varias versiones de Visual Studio instaladas en el mismo equipo. Sin embargo, no puede tener versiones en paralelo de los VSPackages cargados en una única versión de Visual Studio.  
  
 Antes de realizar el VSPackage puede cargarse en las versiones en paralelo de Visual Studio, tenga en cuenta lo siguiente:  
  
-   Debe determinar qué estrategia de implementación en paralelo que desea seguir.  
  
     Para obtener más información, consulte [VSPackages con control de versiones y elegir entre compartir](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   Los formatos de archivo de solución y proyecto deben ajustarse a su estrategia de implementación.  
  
     Para obtener más información, consulte [actualizar proyectos personalizados](../misc/upgrading-custom-projects.md) y [registrar extensiones de nombre de archivo para las implementaciones de Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   El instalador debe controlar la estrategia de implementación para que los componentes con control de versiones, además de componentes compartidos por todas las versiones, están correctamente instalados y registrados.  
  
     Para obtener más información, consulte [Installing VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) y también [componente administración](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Instalar una versión de Visual Studio, también instala una versión correspondiente de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Por ejemplo, la instalación de Visual Studio 2010 y Visual Studio 2012 en el mismo equipo también instala las versiones 4.0 y 4.5 de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], respectivamente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Elección entre VSPackages compartidos y con versiones](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Explica cómo resolver problemas en paralelo en el VSPackage.  
  
 [Registro de extensiones de nombre de archivo para implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Describe cómo el VSPackage puede registrar las asociaciones de archivo en un escenario en paralelo.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Instalar VSPackages](../misc/installing-vspackages.md)  
 Se analiza cómo compilar e instalar VSPackages y cómo admitir usuarios que ejecutan varias versiones de Visual Studio al mismo tiempo.

