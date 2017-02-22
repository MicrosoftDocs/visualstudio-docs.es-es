---
title: "GetFrameworkPath (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkPath (tarea) [MSBuild]"
  - "MSBuild, GetFrameworkPath (tarea)"
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GetFrameworkPath (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Recupera la ruta de acceso a los ensamblados de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Parámetros de la tarea  
 En la siguiente tabla se describen los parámetros de la tarea `GetFrameworkPath`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de .NET Framework versión 1.1, si existe.  En caso contrario, devuelve `null`.|  
|`FrameworkVersion20Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de .NET Framework versión 2.0, si existe.  En caso contrario, devuelve `null`.|  
|`FrameworkVersion30Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de .NET Framework versión 3.0, si existe.  En caso contrario, devuelve `null`.|  
|`FrameworkVersion35Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de .NET Framework versión 3.5, si existe.  En caso contrario, devuelve `null`.|  
|`FrameworkVersion40Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de .NET Framework versión 4.0, si existe.  En caso contrario, devuelve `null`.|  
|`Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los últimos ensamblados de .NET Framework, si alguno está disponible.  En caso contrario, devuelve `null`.|  
  
## Comentarios  
 Si se instalan varias versiones de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], esta tarea devuelve la versión en la que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] está diseñada para ejecutarse.  
  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Ejemplo  
 En el ejemplo siguiente se utiliza la tarea `GetFrameworkPath` para almacenar la ruta de acceso a [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en la propiedad `FrameworkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)