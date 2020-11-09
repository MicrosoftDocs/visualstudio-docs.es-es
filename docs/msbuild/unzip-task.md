---
title: Tarea Unzip | Microsoft Docs
description: Obtenga información sobre los parámetros y el uso de la tarea Unzip de MSBuild, que descomprime un archivo .zip en una ubicación especificada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Unzip
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Unzip task [MSBuild]
- MSBuild, Unzip task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d701f70950bb5a5cb2338007db129ca15d194b77
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046909"
---
# <a name="unzip-task"></a>Tarea Unzip

Descomprime un archivo *.zip* en la ubicación especificada.

>[!NOTE]
>La tarea `Unzip` solo está disponible en MSBuild 15.8 y versiones posteriores.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `Unzip` .

|Parámetro|Descripción|
|---------------|-----------------|
|`DestinationFolder`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido<br /><br /> Especifica la carpeta de destino en la que se va a descomprimir el archivo.|
|`OverwriteReadOnlyFiles`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, sobrescribe los archivos de solo lectura. Tiene como valor predeterminado `false`.|
|`SkipUnchangedFiles`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, omite la descompresión de archivos sin cambios. Tiene como valor predeterminado `true`. La tarea `Unzip` considera que los archivos están sin modificar si tienen el mismo tamaño y la misma hora de última modificación.|
|`SourceFiles`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica uno o varios de los archivos para descomprimir. Cuando se especifican varios archivos, se descomprimen en orden en la misma carpeta.|

## <a name="remarks"></a>Comentarios

 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Ejemplo

 En el siguiente ejemplo se descomprime un archivo y se sobrescriben los archivos de solo lectura.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="UnzipArchive" BeforeTargets="Build">
        <Unzip
            SourceFiles="MyArchive.zip"
            DestinationFolder="$(OutputPath)\unzipped"
            OverwriteReadOnlyFiles="true"
        />
    </Target>

</Project>
```

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
