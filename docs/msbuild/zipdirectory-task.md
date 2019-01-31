---
title: Tarea ZipDirectory | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ZipDirectory
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ZipDirectory task [MSBuild]
- MSBuild, ZipDirectory task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b09c98fb41adcf1d094ca3cf35e9415773e5c292
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54963533"
---
# <a name="zipdirectory-task"></a>Tarea ZipDirectory
Crea un archivo *.zip* desde el contenido de un directorio.

>[!NOTE]
>La tarea `ZipDirectory` solo está disponible en MSBuild 15.8 y versiones posteriores.
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `ZipDirectory` .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`DestinationFile`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido<br /><br /> La ruta de acceso completa al archivo *.zip* que se va a crear.|
|`Overwrite`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, omite el archivo de destino; se sobrescribirá si existe. Tiene como valor predeterminado `false`.|
|`SourceDirectory`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica el directorio desde el que crear un archivo *.zip*.|
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un archivo *.zip* desde el directorio de salida después de compilar un proyecto.
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip" />
    </Target>

</Project>
```
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
