---
title: "Delete (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Delete"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Delete (tarea) [MSBuild]"
  - "MSBuild, Delete (tarea)"
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Delete (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Elimina los archivos especificados.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `Delete`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`DeletedFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los archivos que se eliminaron correctamente.|  
|`Files`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los archivos que se van a eliminar.|  
|`TreatErrorsAsWarnings`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se anotan los errores como advertencias.  El valor predeterminado es `false`.|  
  
## Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Ejemplo  
 En este ejemplo, se elimina el archivo `MyApp.pdb`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <AppName>MyApp</AppName>  
    </PropertyGroup>  
  
    <Target Name="DeleteFiles">  
        <Delete Files="$(AppName).pdb" />  
    </Target>  
</Project>  
```  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)