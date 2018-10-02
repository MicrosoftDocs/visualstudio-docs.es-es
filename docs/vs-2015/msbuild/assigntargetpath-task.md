---
title: Tarea AssignTargetPath| Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63836579d43ed9415d85f987b04b440eb387e95c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574248"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [tarea AssignTargetPath](https://docs.microsoft.com/visualstudio/msbuild/assigntargetpath-task).  
  
  
Esta tarea acepta una archivos de lista de archivos y agrega atributos `<TargetPath>` si no se han especificado ya.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
 En la siguiente tabla se describen los parámetros de la tarea `AssignTargetPath`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`RootFolder`|Parámetro de entrada `string` opcional.<br /><br /> Contiene la ruta de acceso a la carpeta que contiene los vínculos de destino.|  
|`Files`|Parámetro de entrada <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene la lista de entrada de archivos.|  
|`AssignedFiles`|Optional<br /><br /> Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br /> Contiene la lista de archivos resultante.|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se ejecuta la tarea `AssignTargetPath` para configurar un proyecto.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)



