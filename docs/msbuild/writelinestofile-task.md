---
title: "WriteLinesToFile (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, WriteLinesToFile (tarea)"
  - "WriteLinesToFile (tarea) [MSBuild]"
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# WriteLinesToFile (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Escribe las rutas de acceso de los elementos especificados en el archivo de texto especificado.  
  
## Parámetros de la tarea  
 En la siguiente tabla se describen los parámetros de la tarea `WriteLinestoFile`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`File`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica el archivo en el que se escribirán los elementos.|  
|`Lines`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los elementos que se escribirán en el archivo.|  
|`Overwrite`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la tarea sobrescribe cualquier contenido existente en el archivo.|  
|`Encoding`|Parámetro `String` opcional.<br /><br /> Seleccione la codificación de caracteres, por ejemplo, "Unicode."  Vea también <xref:System.Text.Encoding>.|  
  
## Comentarios  
 Si `Overwrite` es `true`, crea un archivo nuevo, escribe el contenido en el archivo y, a continuación, lo cierra.  Si el archivo de destino ya existe, se sobrescribe.  Si `Overwrite` es `false`, agrega el contenido al archivo, creando el archivo de destino, si no existe ya.  
  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Ejemplo  
 En el ejemplo siguiente se utiliza la tarea `WriteLinesToFile` para escribir las rutas de acceso de los elementos en la colección de elementos `MyItems` en el archivo especificado por la colección de elementos `MyTextFile`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)