---
title: "FindUnderPath (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "FindUnderPath (tarea) [MSBuild]"
  - "MSBuild, FindUnderPath (tarea)"
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# FindUnderPath (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Determina los elementos en la colección de elementos especificada que tienen rutas de acceso dentro o debajo de la carpeta especificada.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `FindUnderPath`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Files`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los archivos cuyas rutas de acceso deben compararse con la ruta especificada por el parámetro `Path`.|  
|`InPath`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene los elementos encontrados en la ruta de acceso especificada.|  
|`OutOfPath`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene los elementos no encontrados en la ruta de acceso especificada.|  
|`Path`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica la ruta de la carpeta que se utilizará como referencia.|  
|`UpdateToAbsolutePaths`|Parámetro `Boolean` opcional.<br /><br /> Si es true, se actualizan las rutas de los elementos de salida para que sean rutas absolutas.|  
  
## Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Ejemplo  
 En el siguiente ejemplo se utiliza la tarea `FindUnderPath` para determinar si los archivos contenidos en el elemento `MyFiles` tienen rutas que existen en la ruta especificada por la propiedad `SearchPath`.  Una vez completada la tarea, el elemento `FilesNotFoundInPath` contiene el archivo `File1.txt` y el elemento `FilesFoundInPath` contiene el archivo `File2.txt`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <MyFiles Include="C:\File1.txt" />  
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <SearchPath>C:\Projects\MyProject</SearchPath>  
    </PropertyGroup>  
  
    <Target Name="FindFiles">  
        <FindUnderPath  
            Files="@(MyFiles)"  
            Path="$(SearchPath)">  
            <Output  
                TaskParameter="InPath"  
                ItemName="FilesFoundInPath" />  
            <Output  
                TaskParameter="OutOfPath"  
                ItemName="FilesNotFoundInPath" />  
        </FindUnderPath>  
    </Target>  
  
</Project>  
```  
  
## Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)