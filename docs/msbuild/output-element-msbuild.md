---
title: "Elemento Output (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Output"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Output> (elemento) [MSBuild]"
  - "Output (elemento) [MSBuild]"
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento Output (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Almacena los valores de salida de la tarea en elementos y propiedades.  
  
## Sintaxis  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`TaskParameter`|Atributo necesario.<br /><br /> Nombre del parámetro de salida de la tarea.|  
|`PropertyName`|Se requiere el atributo `PropertyName` o el atributo `ItemName`.<br /><br /> Propiedad que recibe el valor del parámetro de salida de la tarea.  Su proyecto puede hacer referencia a la propiedad con la sintaxis `$(`*PropertyName*`)`.  Este nombre de propiedad puede ser un nuevo nombre de propiedad o un nombre ya definido en el proyecto.<br /><br /> No se puede utilizar este atributo si también se utiliza `ItemName`.|  
|`ItemName`|Se requiere el atributo `PropertyName` o el atributo `ItemName`.<br /><br /> Elemento que recibe el valor del parámetro de salida de la tarea.  Su proyecto puede hacer referencia al elemento con la sintaxis `@(`*ItemName*`)`.  Este nombre de elemento puede ser un nuevo nombre de elemento o un nombre ya definido en el proyecto.<br /><br /> No se puede utilizar este atributo si también se utiliza `PropertyName`.|  
|`Condition`|Atributo opcional.<br /><br /> Condición que se va a evaluar.  Para obtener más información, vea [Condiciones](../msbuild/msbuild-conditions.md).|  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Tarea](../msbuild/task-element-msbuild.md)|Crea y ejecuta una instancia de una tarea de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestra la tarea `Csc` que se está ejecutando en un elemento `Target`.  Los elementos y propiedades pasados a los parámetros de tarea se declaran fuera del ámbito de este ejemplo.  El valor del parámetro de salida `OutputAssembly` se almacena en el elemento `FinalAssemblyName`, y el valor del parámetro de salida `BuildSucceeded` se almacena en la propiedad `BuildWorked`.  Para obtener más información, vea [Tareas](../msbuild/msbuild-tasks.md).  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## Vea también  
 [Referencia de esquemas del archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)