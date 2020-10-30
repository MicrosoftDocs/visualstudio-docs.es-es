---
title: Tarea FindInList | Microsoft Docs
description: Obtenga información sobre cómo usar la tarea FindInList de MSBuild para buscar un elemento con las especificaciones coincidentes en una lista especificada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4afc20b7845f3af71de1fbbb89f074801e08d1d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2020
ms.locfileid: "92435698"
---
# <a name="findinlist-task"></a>FindInList (tarea)

Busca en una lista especificada un elemento con las especificaciones coincidentes.

## <a name="parameters"></a>Parámetros

 En la tabla siguiente se describen los parámetros de [FindInList (tarea)](../msbuild/findinlist-task.md).

|Parámetro|Descripción|
|---------------|-----------------|
|`CaseSensitive`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la búsqueda distingue entre mayúsculas y minúsculas; en caso contrario, no lo hace. El valor predeterminado es `true`.|
|`FindLastMatch`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, devuelve la última coincidencia; en caso contrario, devuelve la primera. El valor predeterminado es `false`.|
|`ItemFound`|Parámetro de salida de solo lectura <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Primer elemento coincidente que se encuentra en la lista, si existe.|
|`ItemSpecToFind`|Parámetro `String` requerido.<br /><br /> Especificación de elemento que se va a buscar.|
|`List`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Lista en la que se va a buscar la especificación de elemento.|
|`MatchFileNameOnly`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, solo se compara con la parte del nombre de archivo de la especificación de elemento; en caso contrario, se compara con toda la especificación de elemento. El valor predeterminado es `true`.|

## <a name="remarks"></a>Comentarios

 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
