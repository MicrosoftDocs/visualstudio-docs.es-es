---
title: Tarea MakeDir | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MakeDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MakeDir task [MSBuild]
- MSBuild, MakeDir task
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 139d52963cfbb332fa084840c665efd3aeb8e88f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200803"
---
# <a name="makedir-task"></a>MakeDir (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Crea directorios y, si es preciso, cualquier directorio primario.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `MakeDir`.  
  
|Parámetro|Description|  
|---------------|-----------------|  
|`Directories`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Conjunto de directorios que se va a crear.|  
|`DirectoriesCreated`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Directorios que crea esta tarea. Si no se pudieron crear algunos directorios, podría no contener todos los elementos que se han pasado en el parámetro `Directories`.|  
  
## <a name="remarks"></a>Observaciones  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [clase base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo de código se usa la tarea `MakeDir` para crear el directorio especificado por la propiedad `OutputDirectory`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <OutputDirectory>\Output\</OutputDirectory>  
    </PropertyGroup>  
  
    <Target Name="CreateDirectories">  
        <MakeDir  
            Directories="$(OutputDirectory)"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Consulte también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
