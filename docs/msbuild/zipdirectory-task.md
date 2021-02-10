---
title: Tarea ZipDirectory | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa la tarea ZipDirectory para crear un archivo .zip a partir del contenido de un directorio.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6b897a33dacdbd52beaabdd9289a010df92a85c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847887"
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
|`Overwrite`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se sobrescribirá el archivo de destino si existe. Tiene como valor predeterminado `false`.|
|`SourceDirectory`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica el directorio desde el que crear un archivo *.zip*.|

## <a name="remarks"></a>Comentarios

 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Ejemplo

 Si se usa como un archivo *.targets* importado, el ejemplo siguiente crea un archivo *.zip* desde el directorio de salida después de compilar un proyecto. Normalmente, la propiedad `$(OutputPath)` se define en un archivo de proyecto de MSBuild, por lo que un archivo de proyecto que importe el siguiente archivo generaría un archivo .zip `output.zip`:

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

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
