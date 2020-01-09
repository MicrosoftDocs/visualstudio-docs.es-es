---
title: Tarea FindAppConfigFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de2b36f1003515a47774eaa40fda390728940324
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591156"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile (tarea)
Busca el archivo *app.config*, si hay alguno, en las listas proporcionadas.

## <a name="parameters"></a>Parámetros
 En la siguiente tabla se describen los parámetros de la tarea `FindAppConfigFile` .

|Parámetro|Descripción|
|---------------|-----------------|
|`AppConfigFile`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica el primer elemento coincidente que se encuentra en la lista, si existe.|
|`PrimaryList`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica la lista principal en la que se va a buscar.|
|`SecondaryList`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica la lista secundaria en la que se va a buscar.|
|`TargetPath`|Parámetro `String` requerido.<br /><br /> Especifica el valor que se va a agregar como metadatos.|

## <a name="remarks"></a>Comentarios
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vea también
- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
