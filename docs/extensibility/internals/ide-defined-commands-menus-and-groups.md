---
title: "Grupos, men&#250;s y comandos definidos por el IDE | Microsoft Docs"
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
  - "comandos, definidos por el entorno"
  - "archivos .vsct, constantes definidas por el entorno"
  - "grupos de comandos definidos por el entorno"
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# Grupos, men&#250;s y comandos definidos por el IDE
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Muchos menús, comandos y grupos de comandos ya están definidos para su uso por el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Estos comandos también están disponibles para su uso al extender [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Buscar comandos definidos por el entorno  
 Los comandos de entorno se definen en un conjunto de cuatro archivos de vsct:  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 Estos archivos se encuentran en *\< ruta de instalación de Visual Studio SDK \>*\\VisualStudioIntegration\\Common\\Inc\\. Estos archivos proporcionan las definiciones y los GUID de los menús y los grupos que pueden usar en el archivo de configuración \(.vsct\) de la tabla de comandos de su paquete VSPackage como contenedores para los menús, grupos y comandos.  
  
## En esta sección  
 [GUID e identificadores de menús de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Proporciona los valores GUID y el ID de menús en la barra de menús de Visual Studio y de los grupos que contienen.  
  
 [GUID e identificadores de las barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Proporciona los valores GUID y el ID de barras de herramientas en el IDE de Visual Studio y de los grupos que contienen.  
  
 [GUID e identificadores de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Proporciona los valores GUID e identificadores de comandos definidos por el IDE de Visual Studio.  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Comandos definidos por el IDE para ampliar sistemas del proyecto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)