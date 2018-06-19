---
title: Tarea FindUnderPath | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 84054917a47fc4d56c107965feebbc353e6de76f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31571612"
---
# <a name="findunderpath-task"></a>FindUnderPath (Tarea)
Determina qué elementos de la colección de elementos especificada tienen rutas de acceso que están en la carpeta especificada o en sus subcarpetas.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `FindUnderPath` .  
  
|Parámetro|Description|  
|---------------|-----------------|  
|`Files`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los archivos cuyas rutas de acceso deben compararse con la ruta de acceso especificada por el parámetro `Path`.|  
|`InPath`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene los elementos que se han encontrado en la ruta de acceso especificada.|  
|`OutOfPath`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene los elementos que no se han encontrado en la ruta de acceso especificada.|  
|`Path`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica la ruta de acceso a la carpeta que se va a usar como referencia.|  
|`UpdateToAbsolutePaths`|Parámetro `Boolean` opcional.<br /><br /> Si es true, las rutas de acceso de los elementos de salida se actualizan para ser absolutas.|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se usa la tarea `FindUnderPath` para determinar si los archivos que se encuentran en el elemento `MyFiles` tienen rutas de acceso que están en la ruta especificada por la propiedad `SearchPath`. Una vez finalizada la tarea, el elemento `FilesNotFoundInPath` contiene el archivo `File1.txt` y el elemento `FilesFoundInPath` contiene el archivo `File2.txt`.  
  
```xml  
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
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)