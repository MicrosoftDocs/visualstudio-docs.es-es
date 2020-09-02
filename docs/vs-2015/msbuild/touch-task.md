---
title: Touch (Tarea) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Touch
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Touch task
- Touch task [MSBuild]
ms.assetid: 8a978645-1393-4904-ae69-42afabd8c109
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf68bf5dada310a23136e431fdaecad3e738d4bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144267"
---
# <a name="touch-task"></a>Touch (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Establece la hora de acceso y de modificación de los archivos.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `Touch`.  
  
|Parámetro|Description|  
|---------------|-----------------|  
|`AlwaysCreate`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, crea cualquier archivo que todavía no existe.|  
|`Files`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica la colección de archivos que se va a modificar.|  
|`ForceTouch`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, obliga a modificar el archivo incluso si es de solo lectura.|  
|`Time`|Parámetro `String` opcional.<br /><br /> Especifica una hora distinta a la hora actual. El formato debe ser aceptable para el método <xref:System.DateTime.Parse%2A>.|  
|`TouchedFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene la colección de elementos que se han modificado correctamente.|  
  
## <a name="remarks"></a>Observaciones  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [clase base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza la tarea `Touch` para cambiar la hora de acceso y de modificación de los archivos especificados en la colección de elementos `Files`, y coloca la lista de archivos que se han modificado correctamente en la colección de elementos `FilesTouched`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
<ItemGroup>  
    <Files Include="File1.cs;File2.cs;File3.cs" />  
</ItemGroup>  
  
    <Target Name="TouchFiles">  
        <Touch  
            Files="@(Files)">  
            <Output  
                TaskParameter="TouchedFiles"  
                ItemName="FilesTouched"/>  
    </Touch>  
</Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
