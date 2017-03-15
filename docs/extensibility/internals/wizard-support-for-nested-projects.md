---
title: "Admite el Asistente para proyectos anidados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Agregar a Asistente de elemento"
  - "proyectos anidados, admite el Asistente"
  - "Asistente para nuevo proyecto"
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Admite el Asistente para proyectos anidados
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El IDE ejecuta a dos asistentes que el proyecto principal para los proyectos anidados pueden implementar: el asistente de **Nuevo proyecto** y el asistente de **Agregar elemento** .  
  
 Si un usuario inicia el asistente para **Nuevo proyecto** seleccionando **agregue el proyecto** y haciendo clic **Nuevo proyecto** en el menú archivo o seleccionando **Agregar** y hace clic con **Nuevo proyecto** en el explorador de soluciones, el IDE ejecuta el comando de **AddProject** y la aplicación de proyecto principal del comando de **AddProject** devuelve un archivo de proyecto de plantilla, o un archivo de asistente \(.vsz\) que tiene un conjunto de parámetros de contexto.  
  
 De igual forma, una aplicación de proyecto principal de los asistentes de **AddItem** devuelve un archivo .vsz que tiene un conjunto diferente de parámetros de contexto.  
  
 Para obtener más información sobre asistentes, vea [Asistente \(. Archivo vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md), [Parámetros de contexto](../../extensibility/internals/context-parameters.md) y [Registro de proyecto y plantillas de elementos](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Proyectos de anidamiento](../../extensibility/internals/nesting-projects.md)