---
title: Tarea Move | Microsoft Docs
description: Obtenga información sobre los parámetros y la configuración de la tarea Move de MSBuild, que traslada los archivos a ubicaciones nuevas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9121c14037ac1bc5740d1f0684f92226a361e6d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918192"
---
# <a name="move-task"></a>Move (tarea)

Mueve los archivos a una nueva ubicación.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `Move`.

|Parámetro|Descripción|
|---------------|-----------------|
|`DestinationFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica la lista de archivos en la que se moverán los archivos de código fuente. Se espera que esta lista sea una asignación unívoca a la lista especificada en el parámetro `SourceFiles`. Es decir, el primer archivo especificado en `SourceFiles` se moverá a la primera ubicación especificada en `DestinationFiles`, etc.|
|`DestinationFolder`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el directorio en el que se desea mover los archivos.|
|`MovedFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene los elementos que se movieron correctamente.|
|`OverwriteReadOnlyFiles`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, se sobrescriben los archivos aunque estén marcados como archivos de solo lectura.|
|`SourceFiles`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los archivos que se van a mover.|

## <a name="remarks"></a>Comentarios

 Se debe especificar el parámetro `DestinationFolder` o `DestinationFiles`, pero no ambos. Si se especifican los dos, la tarea produce un error y se registra un error.

 La tarea `Move` crea carpetas según sea necesario para los archivos de destino deseados.

 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
