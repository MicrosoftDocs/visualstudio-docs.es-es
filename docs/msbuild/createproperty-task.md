---
title: "CreateProperty (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "CreateProperty (tarea) [MSBuild]"
  - "MSBuild, CreateProperty (tarea)"
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# CreateProperty (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Rellena las propiedades con los valores pasados.  Esto permite copiar los valores de una propiedad o cadena a otra.  
  
## Atributos  
 En la siguiente tabla se describen los parámetros de la tarea `CreateProperty`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Value`|Parámetro de salida `String` opcional.<br /><br /> Especifica el valor que se copiará a la nueva propiedad.|  
|`ValueSetByTask`|Parámetro de salida `String` opcional.<br /><br /> Contiene el mismo valor que el parámetro `Value`.  Utilice este parámetro solamente si desea evitar que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] establezca la propiedad de salida cuando omite el destino que la contiene porque los resultados están actualizados.|  
  
## Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Ejemplo  
 El ejemplo siguiente utiliza la tarea `CreateProperty` para crear la propiedad `NewFile` mediante la combinación de los valores de la propiedad `SourceFilename` y `SourceFileExtension`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 Después de ejecutar el proyecto, el valor de la propiedad `NewFile` es `Module1.vb`.  
  
## Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)