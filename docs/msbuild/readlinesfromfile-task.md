---
title: "ReadLinesFromFile (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ReadLinesFromFile"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, ReadLinesFromFile (tarea)"
  - "ReadLinesFromFile (tarea) [MSBuild]"
ms.assetid: a18af929-b53a-4d9e-b7bf-e3d3737ee85f
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# ReadLinesFromFile (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lee una lista de elementos de un archivo de texto.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `ReadLinesFromFile`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`File`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica el archivo que se va a leer.  El archivo debe tener un elemento en cada línea.|  
|`Lines`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene las líneas leídas del archivo.|  
  
## Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Ejemplo  
 En el ejemplo siguiente se utiliza la tarea `ReadLinesFromFile` para crear elementos a partir de una lista en un archivo de texto.  Los elementos leídos desde el archivo se almacenan en la colección de elementos `ItemsFromFile`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
    </ItemGroup>  
  
    <Target Name="ReadFromFile">  
        <ReadLinesFromFile  
            File="@(MyTextFile)" >  
            <Output  
                TaskParameter="Lines"  
                ItemName="ItemsFromFile"/>  
        </ReadLinesFromFile>  
    </Target>  
  
</Project>  
```  
  
## Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Tareas](../msbuild/msbuild-tasks.md)