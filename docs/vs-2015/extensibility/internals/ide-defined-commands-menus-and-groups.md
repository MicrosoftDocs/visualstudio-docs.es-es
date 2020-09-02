---
title: Comandos, menús y grupos definidos por el IDE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 32e8135328c11fd74311371d07645a525426371e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192727"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Grupos, menús y comandos definidos por el IDE
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Muchos menús, comandos y grupos de comandos ya están definidos para su uso en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Estos comandos también están disponibles para su uso al extender [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="finding-environment-defined-commands"></a>Buscar comandos definidos por el entorno  
 Los comandos de entorno se definen en un conjunto de cuatro archivos. Vsct:  
  
- SharedCmdDef. Vsct  
  
- SharedCmdPlace. Vsct  
  
- ShellCmdDef. Vsct  
  
- ShellCmdPlace. Vsct  
  
  Estos archivos se encuentran en *\<Visual Studio SDK installation path>* \VisualStudioIntegration\Common\Inc \\ . Estos archivos proporcionan las definiciones y los GUID de los menús y grupos que puede usar en el archivo de configuración de la tabla de comandos (. Vsct) del VSPackage como contenedores para sus propios menús, grupos y comandos.  
  
## <a name="in-this-section"></a>En esta sección  
 [GUID e identificadores de menús de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Proporciona los valores de identificador y GUID de los menús de la barra de menús de Visual Studio y de los grupos que contienen.  
  
 [GUID e identificadores de barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Proporciona los valores de identificador y GUID de las barras de herramientas en el IDE de Visual Studio y de los grupos que contienen.  
  
 [GUID e identificadores de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Proporciona los valores de identificador y GUID de los comandos definidos por el IDE de Visual Studio.  
  
## <a name="see-also"></a>Consulte también  
 [Tabla de comandos de Visual Studio (. Archivos de Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Comandos definidos por el IDE para la extensión de sistemas de proyecto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
