---
title: "GetReferenceAssemblyPaths (Tarea) | Microsoft Docs"
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
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GetReferenceAssemblyPaths (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Devuelve las rutas de acceso al ensamblado de referencia de los diversos marcos.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `GetReferenceAssemblyPaths`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Parámetro de salida `String[]` opcional.<br /><br /> Devuelve la ruta de acceso, basada en el parámetro `TargetFrameworkMoniker`.  Si `TargetFrameworkMoniker` es nulo o está vacío, esta ruta será `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Parámetro de salida `String[]` opcional.<br /><br /> Devuelve la ruta de acceso, basada en el parámetro `TargetFrameworkMoniker`, sin tener en cuenta la parte del perfil del moniker.  Si `TargetFrameworkMoniker` es nulo o está vacío, esta ruta será `String.Empty`.|  
|`TargetFrameworkMoniker`|Parámetro `String` opcional.<br /><br /> Especifica el moniker de la versión de .NET Framework de destino asociado a las rutas de acceso del ensamblado de referencia.|  
|`RootPath`|Parámetro `String` opcional.<br /><br /> Especifica la ruta de acceso raíz que se va a usar para generar la ruta de acceso al ensamblado de referencia.|  
|`BypassFrameworkInstallChecks`|Parámetro [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True) opcional.<br /><br /> Si es `true`, omite las comprobaciones básicas que realiza `GetReferenceAssemblyPaths` de forma predeterminada para asegurarse de que ciertos marcos en tiempo de ejecución se instalan en función de la versión de .NET Framework de destino.|  
|`TargetFrameworkMonikerDisplayName`|Parámetro de salida `String` opcional.<br /><br /> Especifica el nombre para mostrar del moniker de la versión de .NET Framework de destino.|  
  
## Comentarios  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)