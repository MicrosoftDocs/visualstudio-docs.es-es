---
title: Compatibilidad con varias versiones de Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d571f1be4da45ff5ed6b2538cfb515930bde1de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699472"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Compatibilidad con varias versiones de Visual Studio
El término en *paralelo* significa que puede instalar y mantener varias versiones de un producto en el mismo equipo. Para VSPackages, eso significa que un usuario puede tener varias versiones de Visual Studio instaladas en el mismo equipo. Sin embargo, no se pueden cargar versiones en paralelo de los VSPackages en una sola versión de Visual Studio.

 Antes de hacer que el VSPackage pueda cargarse en versiones en paralelo de Visual Studio, tenga en cuenta lo siguiente:

- Debe determinar qué estrategia de implementación en paralelo desea seguir.

   Para obtener más información, vea [elegir entre VSPackages compartidos y con control de versiones](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Los formatos de archivo de proyecto y de solución deben ajustarse a la estrategia de implementación.

   Para obtener más información, vea [actualizar proyectos personalizados](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) y [registrar extensiones de nombre de archivo para implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- El instalador debe administrar la estrategia de implementación para que los componentes con versión y también los componentes compartidos en todas las versiones se instalen y registren correctamente.

   Para obtener más información, vea [instalar VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) y también [Administración de componentes](../extensibility/internals/component-management.md).

  > [!NOTE]
  > Al instalar una versión de Visual Studio, también se instala una versión correspondiente de la .NET Framework. Por ejemplo, la instalación de Visual Studio 2010 y Visual Studio 2012 en el mismo equipo también instala las versiones 4,0 y 4,5 del .NET Framework, respectivamente.

## <a name="in-this-section"></a>En esta sección
- [Elegir entre VSPackages compartidos y con control de versiones](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Explica cómo resolver problemas en paralelo en el VSPackage.

- [Registro de extensiones de nombre de archivo para implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Describe cómo el VSPackage puede registrar asociaciones de archivo en un escenario en paralelo.

## <a name="related-sections"></a>Secciones relacionadas
- [Instalación de VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
