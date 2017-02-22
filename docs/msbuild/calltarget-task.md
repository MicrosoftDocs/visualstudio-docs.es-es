---
title: "CallTarget (Tarea) | Microsoft Docs"
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
  - "CallTarget (tarea) [MSBuild]"
  - "MSBuild, CallTarget (tarea)"
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CallTarget (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Invoca los destinos especificados en el archivo de proyecto.  
  
## Parámetros de la tarea  
 En la siguiente tabla se describen los parámetros de la tarea `CallTarget`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`RunEachTargetSeparately`|Parámetro de salida `Boolean` opcional.<br /><br /> Si es `true`, se llama al motor [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] una vez por destino.  Si `false`, se llama una vez al motor de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para compilar todos los destinos.  El valor predeterminado es `false`.|  
|`TargetOutputs`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene los resultados de todos los destinos compilados.|  
|`Targets`|Parámetro `String[]` opcional.<br /><br /> Especifica los destinos que se van a compilar.|  
|`UseResultsCache`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, el resultado en la memoria caché se devuelve si está presente.<br /><br /> **Nota** cuando se ejecuta una tarea de MSBuild, su salida se almacena en caché en un ámbito \(nombreDeArchivoDeProyecto, propiedadesGlobales\)\[nombresDeDestino\] como una lista de elementos de compilación.|  
  
## Comentarios  
 Si un destino especificado en `Targets` no se compila correctamente y el valor de `RunEachTargetSeparately` es `true`, la tarea continúa generando los destinos restantes.  
  
 Si desea compilar los destinos predeterminados, utilice la [MSBuild \(Tarea\)](../msbuild/msbuild-task.md) y establezca el parámetro `Projects` en un valor igual a `$(MSBuildProjectFile)`.  
  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Ejemplo  
 En el siguiente ejemplo se llama a `TargetA` desde `CallOtherTargets`.  
  
```  
<Project DefaultTargets="CallOtherTargets"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <Target Name="CallOtherTargets">  
        <CallTarget Targets="TargetA"/>  
    </Target>  
  
    <Target Name="TargetA">  
        <Message Text="Building TargetA..." />  
    </Target>  
  
</Project>  
```  
  
## Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Destinos](../msbuild/msbuild-targets.md)