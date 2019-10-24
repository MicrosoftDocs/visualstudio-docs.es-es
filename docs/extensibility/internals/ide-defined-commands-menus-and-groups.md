---
title: Comandos, menús y grupos definidos por el IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af6d3e180e2b3d5eb2e0f6c85b7488761e160c69
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727298"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Grupos, menús y comandos definidos por el IDE
Muchos menús, comandos y grupos de comandos ya están definidos para su uso en el IDE de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Estos comandos también están disponibles para su uso cuando se extiende [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="finding-environment-defined-commands"></a>Buscar comandos definidos por el entorno
 Los comandos de entorno se definen en un conjunto de cuatro archivos. Vsct:

- SharedCmdDef. Vsct

- SharedCmdPlace. Vsct

- ShellCmdDef. Vsct

- ShellCmdPlace. Vsct

  Estos archivos se encuentran en la *ruta de instalación de \<Visual Studio SDK >* \VisualStudioIntegration\Common\Inc \\. Estos archivos proporcionan las definiciones y los GUID de los menús y grupos que puede usar en el archivo de configuración de la tabla de comandos (. Vsct) del VSPackage como contenedores para sus propios menús, grupos y comandos.

## <a name="in-this-section"></a>En esta sección
- [GUID e identificadores de menús de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Proporciona los valores de identificador y GUID de los menús de la barra de menús de Visual Studio y de los grupos que contienen.

- [GUID e identificadores de las barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Proporciona los valores de identificador y GUID de las barras de herramientas en el IDE de Visual Studio y de los grupos que contienen.

- [GUID e identificadores de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Proporciona los valores de identificador y GUID de los comandos definidos por el IDE de Visual Studio.

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Comandos definidos por el IDE para ampliar sistemas del proyecto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)