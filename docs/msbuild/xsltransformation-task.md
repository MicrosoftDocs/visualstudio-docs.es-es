---
title: XslTransformation (Tarea) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4eb192777b85adbfc270c7cbdb4469548333c5ec
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="xsltransformation-task"></a>XslTransformation (Tarea)
Transforma una entrada XML mediante una transformación XSL o una transformación XSL compilada y la envía a un dispositivo de salida o archivo.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `XslTransformation` .  
  
|Parámetro|Description|  
|---------------|-----------------|  
|`OutputPaths`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los archivos de salida de la transformación XML.|  
|`Parameters`|Parámetro `String` opcional.<br /><br /> Especifica los parámetros del documento de entrada XSLT.|  
|`XmlContent`|Parámetro `String` opcional.<br /><br /> Especifica la entrada XML como una cadena.|  
|`XmlInputPaths`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los archivos de entrada XML.|  
|`XslCompiledDllPath`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el XSLT compilado.|  
|`XslContent`|Parámetro `String` opcional.<br /><br /> Especifica la entrada XSLT como una cadena.|  
|`XslInputPath`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el archivo de entrada XSLT.|  
  
## <a name="remarks"></a>Comentarios  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)