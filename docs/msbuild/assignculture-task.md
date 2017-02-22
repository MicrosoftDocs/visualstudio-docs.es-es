---
title: "AssignCulture (Tarea) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "AssignCulture (tarea) [MSBuild]"
  - "MSBuild, AssignCulture (tarea)"
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# AssignCulture (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta tarea admite, como parte de un nombre de archivo, una lista de elementos que puede contener una cadena de identificador de referencia cultural .NET válido. Asimismo, genera elementos con metadatos denominados `Culture` que contienen el identificador de referencia cultural correspondiente.  Por ejemplo, el nombre de archivo Form1.fr\-fr.resx tiene un identificador de referencia cultural integrado "fr\-fr", por lo que esta tarea generará un elemento con el mismo nombre de archivo y cuyo metadato `Culture` es igual a `fr-fr`.  La tarea también genera una lista de nombres de archivo cuya referencia cultural se ha quitado del nombre de archivo.  
  
## Parámetros de la tarea  
 En la siguiente tabla se describen los parámetros de la tarea `AssignCulture`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AssignedFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene la lista de elementos recibida en el parámetro `Files`, con una entrada de metadatos `Culture` agregada a cada elemento.<br /><br /> Si el elemento de entrada del parámetro `Files` ya contiene una entrada de metadatos `Culture`, se utiliza la entrada de metadatos original.<br /><br /> La tarea solo asigna una entrada de metadatos `Culture` si el nombre de archivo contiene un identificador de referencia cultural válido.  El identificador de referencia cultural debe estar entre los últimos dos puntos del nombre de archivo.|  
|`AssignedFilesWithCulture`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene el subconjunto de los elementos del parámetro `AssignedFiles` que tiene una entrada de metadatos `Culture`.|  
|`AssignedFilesWithNoCulture`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene el subconjunto de los elementos del parámetro `AssignedFiles` que no tiene una entrada de metadatos `Culture`.|  
|`CultureNeutralAssignedFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene la misma lista de elementos generados en el parámetro `AssignedFiles`, excepto que se ha quitado la referencia cultural del nombre de archivo.<br /><br /> La tarea sólo quita la referencia cultural del nombre de archivo si es un identificador de referencia cultural válido.|  
|`Files`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica la lista de archivos con nombres de referencia cultural incrustados a los que se asignará una referencia cultural.|  
  
## Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Ejemplo  
 En el ejemplo siguiente se ejecuta la tarea `AssignCulture` con la colección de elementos `ResourceFiles`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ResourceFiles Include="MyResource1.fr.resx"/>  
        <ResourceFiles Include="MyResource2.XX.resx"/>  
    </ItemGroup>  
  
    <Target Name="Culture">  
        <AssignCulture  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
            <Output TaskParameter="AssignedFilesWithCulture"  
                ItemName="OutAssignedFilesWithCulture"/>  
            <Output TaskParameter="AssignedFilesWithNoCulture"  
                ItemName="OutAssignedFilesWithNoCulture"/>  
            <Output TaskParameter="CultureNeutralAssignedFiles"  
                ItemName="OutCultureNeutralAssignedFiles"/>  
        </AssignCulture>  
    </Target>  
</Project>  
```  
  
 La tabla siguiente describe el valor de los elementos de salida después de la ejecución de la tarea.  Los metadatos del elemento se muestran entre paréntesis después del elemento.  
  
|Colección de elementos|Contenido|  
|----------------------------|---------------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` \(sin metadatos adicionales\)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` \(sin metadatos adicionales\)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (` \(sin metadatos adicionales\)|  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)