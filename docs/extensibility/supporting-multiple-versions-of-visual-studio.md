---
title: Compatibilidad con varias versiones de Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 317ec1f214d18989c3b2c5c27fe9df9309239631
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137825"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Compatibilidad con varias versiones de Visual Studio
El término *side-by-side* significa que puede instalar y mantener varias versiones de un producto en el mismo equipo. Para VSPackages, que significa que un usuario puede tener varias versiones de Visual Studio instaladas en el mismo equipo. Sin embargo, no puede tener versiones side-by-side de sus VSPackages cargados en una única versión de Visual Studio.  
  
 Antes de realizar el VSPackage que se pueda cargar en paralelo para las versiones de Visual Studio, tenga en cuenta lo siguiente:  
  
-   Debe determinar qué estrategia de implementación en paralelo que desea que siga.  
  
     Para obtener más información, consulte [VSPackages con control de versiones y elegir entre compartido](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   Los formatos de archivo de solución y proyecto deben ajustarse a la estrategia de implementación.  
  
     Para obtener más información, consulte [actualizar proyectos personalizados](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) y [registrar extensiones de nombre de archivo para las implementaciones de Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   El instalador debe controlar la estrategia de implementación para que los componentes con control de versiones y también los componentes compartidos por todas las versiones, están correctamente instalados y registrados.  
  
     Para obtener más información, consulte [instalar VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) y también [componente administración](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Instalar una versión de Visual Studio, también instala una versión correspondiente de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Por ejemplo, la instalación de Visual Studio 2010 y Visual Studio 2012 en el mismo equipo también instala las versiones 4.0 y 4.5 de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], respectivamente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Elección entre VSPackages compartidos y con versiones](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Explica cómo resolver problemas en paralelo en el VSPackage.  
  
 [Registro de extensiones de nombre de archivo para implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Describe cómo el VSPackage puede registrar las asociaciones de archivo en un escenario en paralelo.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Instalación de VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)  
