---
title: "Elemento OnError (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#OnError"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<OnError (elemento) [MSBuild]"
  - "OnError (elemento) [MSBuild]"
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Elemento OnError (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hace que uno o varios destinos se ejecuten si el atributo `ContinueOnError` es `false` para una tarea que ha fallado.  
  
## Sintaxis  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Condition`|Atributo opcional.<br /><br /> Condición que se va a evaluar.  Para obtener más información, vea [Condiciones](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Atributo necesario.<br /><br /> Los destinos que se ejecutarán si en una tarea se produce un error.  Los destinos van separados con punto y coma.  Los diversos destinos se ejecutan en el orden especificado.|  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Destino](../msbuild/target-element-msbuild.md)|Elemento contenedor de tareas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Comentarios  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ejecuta el elemento `OnError` si una de las tareas de elemento `Target` emite el atributo `ContinueOnError` establecido en `ErrorAndStop` \(o a `false`\).  Cuando en la tarea se produce un error, se ejecutan los destinos especificados en el atributo `ExecuteTargets`.  Si hay más de un elemento `OnError` en el destino, los elementos `OnError` se ejecutan secuencialmente cuando en la tarea se produce un error.  
  
 Para obtener información sobre el atributo `ContinueOnError` , vea [Elemento Task \(MSBuild\)](../msbuild/task-element-msbuild.md).  Para obtener información sobre los destinos, vea [Destinos](../msbuild/msbuild-targets.md).  
  
## Ejemplo  
 El código siguiente ejecuta las tareas `TaskOne` y `TaskTwo`.  Si se produce un error en `TaskOne`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] evalúa el elemento `OnError` y ejecuta el destino `OtherTarget`.  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## Vea también  
 [Referencia de esquemas del archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Destinos](../msbuild/msbuild-targets.md)