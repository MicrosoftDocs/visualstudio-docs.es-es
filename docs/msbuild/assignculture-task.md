---
title: AssignCulture (Tarea) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AssignCulture task
- AssignCulture task [MSBuild]
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 40fb47caea1b9fcb0d25d45495cf3e3c1d3e04fb
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="assignculture-task"></a>AssignCulture (Tarea)
Esta tarea acepta una lista de elementos que puede contener una cadena de identificador de referencia cultural .NET válida como parte del nombre de archivo y genera elementos que tengan metadatos con el nombre `Culture` que contiene el correspondiente identificador de referencia cultural. Por ejemplo, el nombre de archivo Form1.fr-fr.resx tiene un indicador de referencia cultural "fr-fr" incluido, por lo que esta tarea genera un elemento que tiene el mismo nombre de archivo con los metadatos de `Culture` igual a `fr-fr`. La tarea también genera una lista de nombres de archivo con la referencia cultural que se quitó del nombre de archivo.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
 En la siguiente tabla se describen los parámetros de la tarea `AssignCulture`.  
  
|Parámetro|Description|  
|---------------|-----------------|  
|`AssignedFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene la lista de elementos recibidos en el parámetro `Files`, con una entrada de metadatos `Culture` agregada a cada elemento.<br /><br /> Si el elemento entrante del parámetro `Files` ya contiene una entrada de metadatos `Culture`, se usa la entrada de metadatos original.<br /><br /> La tarea solo asigna una entrada de metadatos `Culture` si el nombre de archivo contiene un identificador de referencia cultural válido. El identificador de referencia cultural debe estar entre los dos últimos puntos en el nombre de archivo.|  
|`AssignedFilesWithCulture`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene el subconjunto de los elementos del parámetro `AssignedFiles` que tienen una entrada de metadatos `Culture`.|  
|`AssignedFilesWithNoCulture`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene el subconjunto de los elementos del parámetro `AssignedFiles` que no tienen una entrada de metadatos `Culture`.|  
|`CultureNeutralAssignedFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene la misma lista de elementos que se produce en el parámetro `AssignedFiles`, pero se ha quitado la referencia cultural del nombre de archivo.<br /><br /> La tarea solo quita la referencia cultural del nombre de archivo si es un identificador de referencia cultural válido.|  
|`Files`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica la lista de archivos con nombres de referencia cultural incluidos a los que se asignará una referencia cultural.|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se ejecuta la tarea `AssignCulture` con la recopilación de objetos `ResourceFiles`.  
  
```xml  
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
  
 En la siguiente tabla se describe el valor de los elementos de salida después de la ejecución de la tarea. Los metadatos del elemento se muestran entre paréntesis después del elemento.  
  
|Colección de elementos.|Contenido|  
|---------------------|--------------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` (sin metadatos adicionales)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` (sin metadatos adicionales)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (` (sin metadatos adicionales)|  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)