---
title: Comandos, menús y grupos definidos por IDE Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6557f49b019a6793698dabe852919ec2e9f28cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707714"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Grupos, menús y comandos definidos por el IDE
Muchos menús, comandos y grupos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comandos ya están definidos para su uso por el IDE. Estos comandos también están disponibles [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]para su uso cuando se extiende .

## <a name="finding-environment-defined-commands"></a>Búsqueda de comandos definidos por el entorno
 Los comandos de entorno se definen en un conjunto de cuatro archivos .vsct:

- SharedCmdDef.vsct

- SharedCmdPlace.vsct

- ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Estos archivos se * \< *encuentran en la ruta de instalación del\\SDK de Visual Studio>. Estos archivos proporcionan las definiciones y GUID de los menús y grupos que puede usar en el archivo de configuración de tabla de comandos (.vsct) de su VSPackage como contenedores para sus propios menús, grupos y comandos.

## <a name="in-this-section"></a>En esta sección
- [GUID e identificadores de menús de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Proporciona los valores GUID e ID de los menús de la barra de menús de Visual Studio y de los grupos que contienen.

- [GUID e identificadores de barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Proporciona los valores GUID e ID de las barras de herramientas en el IDE de Visual Studio y de los grupos que contienen.

- [GUID e identificadores de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Proporciona los valores GUID e ID de los comandos definidos por el IDE de Visual Studio.

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Comandos definidos por el IDE para ampliar sistemas del proyecto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
