---
title: Grupos, menús y comandos definidos por el IDE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 34c41608a90b15538e190be093ed2791a90824f9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857281"
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
 [GUID e identificadores de menús de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Proporciona los valores GUID y el Id. de menús en la barra de menús de Visual Studio y de los grupos que contienen.  
  
 [GUID e identificadores de las barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Proporciona los valores GUID y el Id. de las barras de herramientas del IDE de Visual Studio y de los grupos que contienen.  
  
 [GUID e identificadores de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Proporciona los valores GUID y el identificador de comandos definidos por el IDE de Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Tabla de comandos de Visual Studio (. Archivos Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Comandos definidos por el IDE para ampliar sistemas del proyecto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)