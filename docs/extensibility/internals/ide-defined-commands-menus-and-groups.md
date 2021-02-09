---
title: IDE-Defined comandos, menús y grupos | Microsoft Docs
description: Obtenga información sobre los menús, comandos y grupos de comandos que se definen en el entorno de desarrollo integrado (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e46832803008ea65d0f7ec4f2723a615ba496b94
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840085"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Grupos, menús y comandos definidos por el IDE
Muchos menús, comandos y grupos de comandos ya están definidos para su uso en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Estos comandos también están disponibles para su uso al extender [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="finding-environment-defined-commands"></a>Buscar comandos Environment-Defined
 Los comandos de entorno se definen en un conjunto de cuatro archivos. Vsct:

- SharedCmdDef. Vsct

- SharedCmdPlace. Vsct

- ShellCmdDef. Vsct

- ShellCmdPlace. Vsct

  Estos archivos se encuentran en *\<Visual Studio SDK installation path>* \VisualStudioIntegration\Common\Inc \\ . Estos archivos proporcionan las definiciones y los GUID de los menús y grupos que puede usar en el archivo de configuración de la tabla de comandos (. Vsct) del VSPackage como contenedores para sus propios menús, grupos y comandos.

## <a name="in-this-section"></a>En esta sección
- [GUID e identificadores de menús de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Proporciona los valores de identificador y GUID de los menús de la barra de menús de Visual Studio y de los grupos que contienen.

- [GUID e identificadores de barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Proporciona los valores de identificador y GUID de las barras de herramientas en el IDE de Visual Studio y de los grupos que contienen.

- [GUID e identificadores de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Proporciona los valores de identificador y GUID de los comandos definidos por el IDE de Visual Studio.

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Comandos definidos por el IDE para ampliar sistemas del proyecto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
