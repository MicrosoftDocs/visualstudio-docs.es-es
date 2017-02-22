---
title: "GenerateTrustInfo (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GenerateTrustInfo (tarea) [MSBuild]"
  - "MSBuild, GenerateTrustInfo (tarea)"
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GenerateTrustInfo (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Genera la información de confianza de la aplicación a partir del manifiesto base y de los parámetros `ExcludedPermissions` y `TargetZone`.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `GenerateTrustInfo`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`ApplicationDependencies`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los ensamblados dependientes.|  
|`BaseManifest`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el manifiesto base a partir del cual se va a generar la información de confianza de la aplicación.|  
|`ExcludedPermissions`|Parámetro `String` opcional.<br /><br /> Especifica uno o varios valores de identidad de permiso separados por un punto y coma, que se van a excluir del conjunto de permisos predeterminado de la zona.|  
|`TargetZone`|Parámetro `String` opcional.<br /><br /> Especifica el conjunto de permisos predeterminados de una zona, que se obtiene de la directiva del equipo.|  
|`TrustInfoFile`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica el archivo que contiene la información sobre la confianza de seguridad de la aplicación.|  
  
## Comentarios  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)