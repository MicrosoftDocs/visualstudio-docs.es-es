---
title: "Agregar proyecto y plantillas de elemento de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos [Visual Studio SDK], agregar"
  - "elementos de proyecto [Visual Studio], agregar"
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Agregar proyecto y plantillas de elemento de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cuando crea posee los tipos de proyecto, debe proporcionar compatibilidad para agregar nuevos proyectos y elementos de proyecto utilizando los cuadros de diálogo estándar del entorno de desarrollo \(IDE\) integrado de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Los temas siguientes describen técnicas distintas para agregar proyectos y elementos de proyecto.  
  
## En esta sección  
 [Contexto de proyecto](../../extensibility/internals/project-context.md)  
 Explica que el proyecto proporciona la mayor parte de la información de contexto del transpira en el entorno.  
  
 [Prioridad del proyecto](../../extensibility/internals/project-priority.md)  
 Explica que un elemento de proyecto suele ser un miembro de un proyecto para evitar la ambigüedad sobre la que se utiliza el proyecto para abrir el elemento.  
  
 [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md)  
 Proporciona información sobre los dos tipos de editores que se pueden utilizar para abrir archivos en un proyecto y el rol el proyecto cumplen en determinar qué editor para utilizar cuando se abre un elemento de proyecto.  
  
 [Registro de proyecto y plantillas de elementos](../../extensibility/internals/registering-project-and-item-templates.md)  
 Explica lo que ocurre cuando se crea un proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  
  
 [Agregar elementos a la para agregar elementos nuevos cuadros de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Explica el proceso de agregar elementos al cuadro de diálogo de **Agregar nuevo elemento** .  
  
 [Agregar directorios en el cuadro de diálogo nuevo proyecto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 proporciona un ejemplo de registrar un nuevo directorio que contenga las plantillas personalizadas creadas disponible por un VSPackage.  
  
 [Agregar directorios a la Add New Item Dialog Box](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Proporciona un ejemplo de registrar un nuevo conjunto de directorios para el cuadro de diálogo de **Agregar nuevo elemento** .  
  
 [Comandos definidos por el IDE para ampliar sistemas del proyecto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Muestra diferentes tipos de elementos de comando utilizados para los sistemas de proyectos que extienden.  
  
 [CATID para los objetos que se utilizan normalmente para extender proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Muestra CATIDs para los objetos que se usan para extender [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], y los sistemas de proyectos de[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .  
  
## Secciones relacionadas  
 [Cómo: abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md)  
 Proporciona instrucciones paso a paso para abrir un elemento enlazado intrínseco a un editor específico de un proyecto.  
  
 [Cómo: abrir editores estándares](../../extensibility/how-to-open-standard-editors.md)  
 Proporciona instrucciones paso a paso para abrir un editor estándar.  
  
 [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)  
 Proporciona vínculos a temas conceptuales de subtipo del proyecto.  Los subtipos de proyecto extienden [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] existente y los proyectos de[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .  
  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona vínculos a temas adicionales que proporcionan información sobre cómo diseñar nuevos tipos de proyecto.