---
title: Grupos, menús y comandos definidos por el IDE | Documentos de Microsoft
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
ms.openlocfilehash: 5158a9d1a06ec6f08c67777e4f1ce2e4d37220e3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315660"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Grupos, menús y comandos definidos por el IDE
Muchos de los menús, comandos y grupos de comandos ya están definidos para su uso por el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Estos comandos también están disponibles para su uso cuando se amplía [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="finding-environment-defined-commands"></a>Buscar comandos definidos en el entorno
 Los comandos de entorno se definen en un conjunto de cuatro archivos de vsct:

- SharedCmdDef.vsct

- SharedCmdPlace.vsct

- ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Estos archivos se encuentran en  *\<ruta de instalación de Visual Studio SDK >* \VisualStudioIntegration\Common\Inc\\. Estos archivos proporcionan las definiciones y los GUID de los menús y los grupos que pueden usar en el archivo de configuración (.vsct) de la tabla de comandos del paquete de VS como contenedores para sus propios menús, grupos y comandos.

## <a name="in-this-section"></a>En esta sección
- [GUID e identificadores de menús de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Proporciona los valores GUID y el Id. de menús en la barra de menús de Visual Studio y de los grupos que contienen.

- [GUID e identificadores de las barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Proporciona los valores GUID y el Id. de las barras de herramientas del IDE de Visual Studio y de los grupos que contienen.

- [GUID e identificadores de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Proporciona los valores GUID y el identificador de comandos definidos por el IDE de Visual Studio.

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Comandos definidos por el IDE para ampliar sistemas del proyecto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)